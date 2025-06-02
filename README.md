
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>立体木鱼·功德积累</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            background-color: #f8f4e8;
            font-family: "SimSun", "宋体", serif;
            touch-action: manipulation;
            user-select: none;
            height: 100vh;
        }
        canvas {
            display: block;
            position: fixed;
            top: 0;
            left: 0;
        }
        #merit-counter {
            position: fixed;
            top: 20px;
            right: 20px;
            font-size: 24px;
            color: #5c3a21;
            text-shadow: 1px 1px 2px rgba(255,255,255,0.5);
            background: rgba(255,255,255,0.3);
            padding: 5px 15px;
            border-radius: 20px;
            border: 1px solid rgba(92,58,33,0.3);
        }
        #instructions {
            position: fixed;
            bottom: 20px;
            left: 0;
            right: 0;
            text-align: center;
            font-size: 18px;
            color: #5c3a21;
            background: rgba(255,255,255,0.3);
            padding: 10px;
            margin: 0 20px;
            border-radius: 20px;
            border: 1px solid rgba(92,58,33,0.3);
        }
        #background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #f8f4e8 0%, #e8e0d0 100%);
            z-index: -2;
        }
        #ink-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><path fill="%23e8e0d0" d="M30,10 Q50,0 70,10 T90,30 Q100,50 90,70 T70,90 Q50,100 30,90 T10,70 Q0,50 10,30 T30,10" opacity="0.05"/></svg>');
            background-size: 200px 200px;
            z-index: -1;
            opacity: 0.3;
        }
    </style>
</head>
<body>
    <div id="background"></div>
    <div id="ink-bg"></div>
    <canvas id="gameCanvas"></canvas>
    <div id="merit-counter">功德: 0</div>
    <div id="instructions">暴打老五-静心解压</div>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const meritCounter = document.getElementById('merit-counter');
        
        // 设置画布大小为窗口大小
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        // 游戏状态
        let merit = 0;
        let particles = [];
        let lastClickTime = 0;
        let clickStreak = 0;
        let backgroundParticles = [];
        
        // 木鱼位置和大小
        const muyu = {
            x: canvas.width / 2,
            y: canvas.height / 2,
            radius: Math.min(canvas.width, canvas.height) * 0.2,
            isHit: false,
            hitTime: 0,
            rotation: 0,
            wobble: 0
        };
        
        // 创建背景水墨粒子
        function createBackgroundParticles() {
            backgroundParticles = [];
            const particleCount = Math.floor((canvas.width * canvas.height) / 5000);
            
            for (let i = 0; i < particleCount; i++) {
                backgroundParticles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 15 + 5,
                    opacity: Math.random() * 0.1 + 0.05,
                    speed: Math.random() * 0.2 + 0.1,
                    angle: Math.random() * Math.PI * 2,
                    rotation: Math.random() * Math.PI * 2,
                    rotationSpeed: (Math.random() - 0.5) * 0.01
                });
            }
        }
        
        // 水墨粒子类
        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.size = Math.random() * 15 + 5;
                this.baseSize = this.size;
                this.color = color || this.getRandomInkColor();
                this.density = (Math.random() * 30) + 1;
                this.velocity = {
                    x: (Math.random() - 0.5) * 10,
                    y: (Math.random() - 0.5) * 10
                };
                this.life = 100;
                this.decay = Math.random() * 0.5 + 0.1;
                this.angle = Math.random() * Math.PI * 2;
                this.rotationSpeed = (Math.random() - 0.5) * 0.1;
                this.waveFactor = Math.random() * 0.1;
                this.waveSpeed = Math.random() * 0.05;
                this.waveOffset = Math.random() * Math.PI * 2;
            }
            
            getRandomInkColor() {
                const colors = ['#3a2511', '#5c3a21', '#8b5a2b', '#4a3520', '#2c1d10'];
                return colors[Math.floor(Math.random() * colors.length)];
            }
            
            update() {
                this.angle += this.rotationSpeed;
                this.waveOffset += this.waveSpeed;
                
                // 更自然的运动
                this.velocity.x *= 0.98;
                this.velocity.y *= 0.98;
                
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                
                // 添加一些波动效果
                this.x += Math.sin(this.waveOffset) * this.waveFactor;
                this.y += Math.cos(this.waveOffset) * this.waveFactor;
                
                this.life -= this.decay;
                this.size = this.baseSize * (this.life / 100);
                
                return this.life > 0;
            }
            
            draw() {
                ctx.save();
                ctx.globalAlpha = this.life / 100 * 0.7;
                ctx.fillStyle = this.color;
                ctx.beginPath();
                
                // 更自然的水墨形状
                const points = [];
                const pointCount = 5 + Math.floor(Math.random() * 5);
                const irregularity = 0.3 + Math.random() * 0.3;
                
                for (let i = 0; i < pointCount; i++) {
                    const angle = (i / pointCount) * Math.PI * 2 + this.angle;
                    const radius = this.size * (1 - irregularity + Math.random() * irregularity * 2);
                    points.push({
                        x: this.x + Math.cos(angle) * radius,
                        y: this.y + Math.sin(angle) * radius
                    });
                }
                
                // 绘制不规则形状
                ctx.moveTo(points[0].x, points[0].y);
                for (let i = 1; i < points.length; i++) {
                    const p = points[i];
                    const prev = points[i-1];
                    const cpX = (prev.x + p.x) / 2;
                    const cpY = (prev.y + p.y) / 2;
                    ctx.quadraticCurveTo(cpX, cpY, p.x, p.y);
                }
                ctx.closePath();
                ctx.fill();
                
                ctx.restore();
            }
        }
        
        // 创建水墨粒子
        function createParticles(x, y, count, color) {
            for (let i = 0; i < count; i++) {
                particles.push(new Particle(x, y, color));
            }
        }
        
        // 绘制立体木鱼
        function drawMuyu() {
            const now = Date.now();
            const hitEffectDuration = 300; // 击中效果持续时间(ms)
            const hitProgress = Math.min(1, (now - muyu.hitTime) / hitEffectDuration);
            
            ctx.save();
            ctx.translate(muyu.x, muyu.y);
            
            // 木鱼摆动效果
            if (muyu.isHit && hitProgress < 0.3) {
                muyu.wobble = Math.sin(hitProgress * Math.PI * 5) * 0.2;
            } else {
                muyu.wobble *= 0.9;
            }
            ctx.rotate(muyu.wobble);
            
            // 木鱼旋转
            muyu.rotation += 0.002;
            ctx.rotate(muyu.rotation);
            
            // 木鱼主体 - 3D效果
            const outerRadius = muyu.radius;
            const innerRadius = outerRadius * 0.7;
            const highlightRadius = outerRadius * 0.3;
            
            // 底部阴影
            ctx.beginPath();
            ctx.arc(0, 0, outerRadius * 1.05, 0, Math.PI * 2);
            ctx.fillStyle = 'rgba(60, 35, 15, 0.2)';
            ctx.fill();
            
            // 木鱼主体渐变
            const gradient = ctx.createRadialGradient(
                0, 0, highlightRadius,
                0, 0, outerRadius
            );
            
            const baseColor = muyu.isHit ? '#d4a373' : '#8b5a2b';
            const shadowColor = muyu.isHit ? '#5c3a21' : '#3a2511';
            
            gradient.addColorStop(0, baseColor);
            gradient.addColorStop(0.7, shadowColor);
            gradient.addColorStop(1, '#2c1d10');
            
            // 木鱼主体
            ctx.beginPath();
            ctx.arc(0, 0, outerRadius, 0, Math.PI * 2);
            ctx.fillStyle = gradient;
            ctx.fill();
            
            // 高光效果
            ctx.beginPath();
            ctx.arc(outerRadius * 0.3, -outerRadius * 0.3, highlightRadius * 0.8, 0, Math.PI * 2);
            const highlightGradient = ctx.createRadialGradient(
                outerRadius * 0.3, -outerRadius * 0.3, 0,
                outerRadius * 0.3, -outerRadius * 0.3, highlightRadius * 0.8
            );
            highlightGradient.addColorStop(0, 'rgba(255, 255, 255, 0.3)');
            highlightGradient.addColorStop(1, 'rgba(255, 255, 255, 0)');
            ctx.fillStyle = highlightGradient;
            ctx.fill();
            
            // 木鱼纹理
            if (!muyu.isHit || hitProgress > 0.5) {
                ctx.strokeStyle = '#5c3a21';
                ctx.lineWidth = 2;
                
                // 中心圆
                ctx.beginPath();
                ctx.arc(0, 0, innerRadius, 0, Math.PI * 2);
                ctx.stroke();
                
                // 纹理线
                for (let i = 0; i < 8; i++) {
                    const angle = (i / 8) * Math.PI * 2;
                    ctx.beginPath();
                    ctx.moveTo(0, 0);
                    ctx.lineTo(
                        Math.cos(angle) * outerRadius,
                        Math.sin(angle) * outerRadius
                    );
                    ctx.stroke();
                }
                
                // 木鱼边缘装饰
                ctx.beginPath();
                ctx.arc(0, 0, outerRadius * 0.95, 0, Math.PI * 2);
                ctx.strokeStyle = '#5c3a21';
                ctx.lineWidth = 3;
                ctx.stroke();
            }
            
            // 击中效果
            if (muyu.isHit && hitProgress < 1) {
                const scale = 1 + (1 - hitProgress) * 0.1;
                ctx.beginPath();
                ctx.arc(0, 0, outerRadius * scale, 0, Math.PI * 2);
                ctx.strokeStyle = `rgba(255, 230, 180, ${1 - hitProgress})`;
                ctx.lineWidth = 5 * (1 - hitProgress);
                ctx.stroke();
            } else if (muyu.isHit) {
                muyu.isHit = false;
            }
            
            ctx.restore();
        }
        
        // 绘制背景水墨粒子
        function drawBackgroundParticles() {
            ctx.save();
            
            for (const p of backgroundParticles) {
                p.rotation += p.rotationSpeed;
                p.x += Math.cos(p.angle) * p.speed;
                p.y += Math.sin(p.angle) * p.speed;
                
                // 边界检查
                if (p.x < -p.size) p.x = canvas.width + p.size;
                if (p.x > canvas.width + p.size) p.x = -p.size;
                if (p.y < -p.size) p.y = canvas.height + p.size;
                if (p.y > canvas.height + p.size) p.y = -p.size;
                
                ctx.globalAlpha = p.opacity;
                ctx.fillStyle = '#5c3a21';
                ctx.save();
                ctx.translate(p.x, p.y);
                ctx.rotate(p.rotation);
                
                // 绘制不规则水墨形状
                ctx.beginPath();
                const points = 5 + Math.floor(Math.random() * 3);
                for (let i = 0; i < points; i++) {
                    const angle = (i / points) * Math.PI * 2;
                    const radius = p.size * (0.7 + Math.random() * 0.3);
                    if (i === 0) {
                        ctx.moveTo(Math.cos(angle) * radius, Math.sin(angle) * radius);
                    } else {
                        ctx.lineTo(Math.cos(angle) * radius, Math.sin(angle) * radius);
                    }
                }
                ctx.closePath();
                ctx.fill();
                
                ctx.restore();
            }
            
            ctx.restore();
        }
        
        // 绘制功德数字效果
        function drawMeritEffects() {
            const now = Date.now();
            const effectDuration = 1000; // 效果持续时间(ms)
            
            // 更新和绘制主粒子
            for (let i = particles.length - 1; i >= 0; i--) {
                const p = particles[i];
                if (!p.update()) {
                    particles.splice(i, 1);
                } else {
                    p.draw();
                }
            }
            
            // 连击效果
            if (clickStreak > 3 && now - lastClickTime < effectDuration) {
                const progress = (now - lastClickTime) / effectDuration;
                const alpha = 1 - progress;
                const size = 30 + progress * 20;
                const yOffset = -muyu.radius - 70 - progress * 30;
                
                ctx.save();
                ctx.font = `bold ${size}px "SimSun", "宋体", serif`;
                ctx.fillStyle = `rgba(92, 58, 33, ${alpha})`;
                ctx.textAlign = 'center';
                ctx.textBaseline = 'middle';
                ctx.fillText(`${clickStreak}连击`, muyu.x, muyu.y + yOffset);
                
                // 连击文字阴影
                ctx.fillStyle = `rgba(255, 230, 180, ${alpha * 0.7})`;
                ctx.fillText(`${clickStreak}连击`, muyu.x + 2, muyu.y + yOffset + 2);
                ctx.restore();
            }
            
            // 功德数字上升效果
            if (now - lastClickTime < 800 && merit > 0) {
                const progress = (now - lastClickTime) / 800;
                const alpha = 1 - progress * 0.7;
                const yOffset = -progress * 100;
                
                ctx.save();
                ctx.font = `24px "SimSun", "宋体", serif`;
                ctx.fillStyle = `rgba(92, 58, 33, ${alpha})`;
                ctx.textAlign = 'center';
                ctx.textBaseline = 'middle';
                ctx.fillText(`功德 +${clickStreak}`, muyu.x, muyu.y - muyu.radius - 30 + yOffset);
                ctx.restore();
            }
        }
        
        // 游戏循环
        function gameLoop() {
            // 清空画布
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            // 绘制所有元素
            drawBackgroundParticles();
            drawMuyu();
            drawMeritEffects();
            
            requestAnimationFrame(gameLoop);
        }
        
        // 处理点击事件
        function handleClick(e) {
            const now = Date.now();
            const x = e.clientX || (e.touches && e.touches[0].clientX);
            const y = e.clientY || (e.touches && e.touches[0].clientY);
            
            if (!x || !y) return;
            
            // 检查是否点击了木鱼
            const distance = Math.sqrt((x - muyu.x) ** 2 + (y - muyu.y) ** 2);
            if (distance <= muyu.radius) {
                // 计算连击
                if (now - lastClickTime < 500) { // 500ms内算连击
                    clickStreak++;
                } else {
                    clickStreak = 1;
                }
                lastClickTime = now;
                
                // 更新功德
                merit += clickStreak; // 连击加成
                meritCounter.textContent = `功德: ${merit}`;
                
                // 木鱼击中效果
                muyu.isHit = true;
                muyu.hitTime = now;
                
                // 创建水墨粒子 - 全屏分布
                const particleCount = 20 + clickStreak * 5;
                for (let i = 0; i < particleCount; i++) {
                    // 从点击点向外扩散
                    const angle = Math.random() * Math.PI * 2;
                    const distance = Math.random() * muyu.radius * 0.7;
                    const px = muyu.x + Math.cos(angle) * distance;
                    const py = muyu.y + Math.sin(angle) * distance;
                    
                    createParticles(px, py, 1);
                }
                
                // 创建功德数字粒子
                for (let i = 0; i < 5; i++) {
                    const p = new Particle(
                        muyu.x + (Math.random() - 0.5) * 30,
                        muyu.y - muyu.radius * 0.7 + (Math.random() - 0.5) * 20,
                        '#8b5a2b'
                    );
                    p.velocity.y = -3 - Math.random() * 4;
                    p.velocity.x = (Math.random() - 0.5) * 4;
                    p.size = 15 + Math.random() * 10;
                    p.decay = 0.2 + Math.random() * 0.2;
                    particles.push(p);
                }
                
                // 播放木鱼声音 (简单版本，实际使用时可以取消注释并添加音频文件)
                // const audio = new Audio('muyu.mp3');
                // audio.volume = 0.3 + Math.min(clickStreak / 10, 0.7);
                // audio.play().catch(e => console.log('音频播放失败:', e));
            }
        }
        
        // 事件监听
        canvas.addEventListener('click', handleClick);
        canvas.addEventListener('touchstart', handleClick);
        
        // 窗口大小调整
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            muyu.x = canvas.width / 2;
            muyu.y = canvas.height / 2;
            muyu.radius = Math.min(canvas.width, canvas.height) * 0.2;
            createBackgroundParticles();
        });
        
        // 初始化背景粒子
        createBackgroundParticles();
        
        // 启动游戏
        gameLoop();
    </script>
</body>
</html>
