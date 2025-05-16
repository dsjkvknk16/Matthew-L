
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Matthew Louis - Luxury Real Estate Strategist with Wharton PhD expertise in high-end property investment and optimization">
    <title>Matthew Louis | Luxury Real Estate Strategist</title>
    
    <!-- Preload critical assets -->
    <link rel="preload" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" as="style">
    <link rel="preload" href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;700&family=Montserrat:wght@300;400;600&display=swap" as="style">
    
    <!-- Favicon -->
    <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
    <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
    <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
    <link rel="manifest" href="/site.webmanifest">
    
    <!-- Fonts -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=Montserrat:wght@300;400;500;600&display=swap" rel="stylesheet">
    
    <!-- AOS Animation -->
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    
    <style>
        :root {
            --ivory: #F9F7F5;
            --charcoal: #1E1E1E;
            --gold: #C4A265;
            --taupe: #8B7D6B;
            --slate: #6E7F80;
            --transition: all 0.6s cubic-bezier(0.77, 0, 0.175, 1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        html {
            scroll-behavior: smooth;
        }
        
        body {
            font-family: 'Montserrat', -apple-system, BlinkMacSystemFont, sans-serif;
            margin: 0;
            padding: 0;
            color: var(--charcoal);
            background-color: var(--ivory);
            display: flex;
            min-height: 100vh;
            overflow-x: hidden;
            line-height: 1.6;
            font-weight: 400;
            text-rendering: optimizeLegibility;
            -webkit-font-smoothing: antialiased;
        }
        
        /* Navigation */
        nav {
            width: 100px;
            background: var(--charcoal);
            color: white;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 60px 0;
            position: fixed;
            height: 100vh;
            z-index: 1000;
            box-shadow: 5px 0 30px rgba(0,0,0,0.2);
            transition: var(--transition);
        }
        
        .nav-logo {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            object-fit: cover;
            margin-bottom: 60px;
            border: 2px solid var(--gold);
            transition: var(--transition);
        }
        
        .nav-menu {
            display: flex;
            flex-direction: column;
            gap: 40px;
        }
        
        .nav-item {
            color: var(--taupe);
            font-size: 1.4rem;
            transition: var(--transition);
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .nav-label {
            font-size: 0.7rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            opacity: 0;
            position: absolute;
            bottom: -20px;
            transition: var(--transition);
        }
        
        .nav-item:hover, .nav-item.active {
            color: var(--gold);
        }
        
        .nav-item:hover .nav-label,
        .nav-item.active .nav-label {
            opacity: 1;
            bottom: -25px;
        }
        
        .nav-item.active::after {
            content: "";
            position: absolute;
            right: -15px;
            top: 50%;
            transform: translateY(-50%);
            width: 3px;
            height: 20px;
            background: var(--gold);
        }
        
        /* Main Content */
        main {
            margin-left: 100px;
            flex: 1;
            display: flex;
            overflow-x: auto;
            scroll-snap-type: x mandatory;
            scroll-behavior: smooth;
            -webkit-overflow-scrolling: touch;
        }
        
        section {
            min-width: 100vw;
            height: 100vh;
            scroll-snap-align: start;
            padding: 80px;
            box-sizing: border-box;
            position: relative;
            overflow-y: auto;
        }
        
        /* Home Section */
        #home {
            display: flex;
            align-items: center;
            background: linear-gradient(rgba(30,30,30,0.92), rgba(30,30,30,0.92)), 
                        url('https://images.unsplash.com/photo-1600585154340-be6161a56a0c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1800&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            color: white;
        }
        
        .hero-content {
            max-width: 700px;
            padding-left: 5%;
        }
        
        .hero-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 4.5rem;
            font-weight: 700;
            margin: 0 0 25px;
            line-height: 1.05;
            letter-spacing: 1px;
        }
        
        .hero-subtitle {
            font-size: 1.3rem;
            color: var(--gold);
            margin-bottom: 40px;
            letter-spacing: 3px;
            text-transform: uppercase;
            position: relative;
            display: inline-block;
        }
        
        .hero-subtitle::after {
            content: "";
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 60px;
            height: 2px;
            background: var(--gold);
        }
        
        .hero-text {
            font-size: 1.15rem;
            line-height: 1.9;
            margin-bottom: 50px;
            opacity: 0.85;
            max-width: 600px;
        }
        
        .cta-button {
            display: inline-block;
            padding: 18px 40px;
            background: transparent;
            color: var(--gold);
            border: 1px solid var(--gold);
            font-size: 0.9rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            text-decoration: none;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }
        
        .cta-button::before {
            content: "";
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: var(--gold);
            transition: var(--transition);
            z-index: -1;
        }
        
        .cta-button:hover {
            color: var(--charcoal);
        }
        
        .cta-button:hover::before {
            left: 0;
        }
        
        .signature {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2rem;
            color: var(--gold);
            margin-top: 60px;
            position: relative;
        }
        
        .signature::before {
            content: "";
            position: absolute;
            top: -20px;
            left: 0;
            width: 100px;
            height: 1px;
            background: rgba(255,255,255,0.3);
        }
        
        /* About Section */
        #about {
            display: flex;
            align-items: center;
            gap: 100px;
            padding: 80px 10%;
        }
        
        .profile-image-container {
            flex: 0 0 450px;
            position: relative;
        }
        
        .profile-image {
            width: 100%;
            height: 600px;
            object-fit: cover;
            box-shadow: 30px 30px 0 var(--gold);
            position: relative;
            z-index: 1;
        }
        
        .profile-image::after {
            content: "";
            position: absolute;
            top: 20px;
            left: 20px;
            right: -20px;
            bottom: -20px;
            border: 1px solid var(--gold);
            z-index: -1;
        }
        
        .about-content {
            flex: 1;
        }
        
        .section-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2.8rem;
            color: var(--gold);
            margin-bottom: 40px;
            position: relative;
            display: inline-block;
        }
        
        .section-title::after {
            content: "";
            position: absolute;
            bottom: -15px;
            left: 0;
            width: 80px;
            height: 2px;
            background: var(--gold);
        }
        
        .about-text {
            line-height: 1.9;
            margin-bottom: 30px;
            font-size: 1.15rem;
            opacity: 0.9;
        }
        
        .highlight {
            color: var(--gold);
            font-weight: 500;
            position: relative;
        }
        
        .highlight::after {
            content: "";
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 100%;
            height: 6px;
            background: rgba(196, 162, 101, 0.2);
            z-index: -1;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
            margin-top: 60px;
        }
        
        .stat-item {
            text-align: center;
            padding: 30px 20px;
            background: rgba(249, 247, 245, 0.7);
            border-radius: 3px;
        }
        
        .stat-number {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2.5rem;
            font-weight: 600;
            color: var(--gold);
            margin-bottom: 10px;
        }
        
        .stat-label {
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            opacity: 0.7;
        }
        
        /* Services Section */
        #services {
            background: var(--charcoal);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 100px 10%;
        }
        
        .services-header {
            margin-bottom: 80px;
            max-width: 600px;
        }
        
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
        }
        
        .service-card {
            background: rgba(255,255,255,0.03);
            padding: 50px 40px;
            border-top: 3px solid var(--gold);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }
        
        .service-card::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(196, 162, 101, 0.03) 0%, rgba(196, 162, 101, 0) 100%);
            z-index: 0;
            transition: var(--transition);
            opacity: 0;
        }
        
        .service-card:hover {
            transform: translateY(-10px);
            background: rgba(255,255,255,0.05);
        }
        
        .service-card:hover::before {
            opacity: 1;
        }
        
        .service-icon {
            font-size: 2.8rem;
            color: var(--gold);
            margin-bottom: 30px;
            position: relative;
            z-index: 1;
        }
        
        .service-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.6rem;
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
        }
        
        .service-description {
            opacity: 0.8;
            position: relative;
            z-index: 1;
        }
        
        /* Contact Section */
        #contact {
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(rgba(249,247,245,0.93), rgba(249,247,245,0.93)), 
                        url('https://images.unsplash.com/photo-1493809842364-78817add7ffb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1800&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            padding: 100px;
        }
        
        .contact-container {
            display: flex;
            max-width: 1200px;
            width: 100%;
            box-shadow: 0 30px 60px rgba(0,0,0,0.1);
        }
        
        .contact-info {
            flex: 1;
            background: var(--charcoal);
            color: white;
            padding: 80px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .contact-form {
            flex: 1;
            background: white;
            padding: 80px;
        }
        
        .info-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2.2rem;
            color: var(--gold);
            margin-bottom: 40px;
        }
        
        .info-item {
            margin-bottom: 30px;
            display: flex;
            align-items: flex-start;
        }
        
        .info-icon {
            color: var(--gold);
            font-size: 1.2rem;
            margin-right: 20px;
            margin-top: 5px;
        }
        
        .info-content h3 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.3rem;
            margin-bottom: 10px;
        }
        
        .info-content p, .info-content a {
            opacity: 0.8;
            color: white;
            text-decoration: none;
            transition: var(--transition);
        }
        
        .info-content a:hover {
            color: var(--gold);
        }
        
        .form-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2.2rem;
            color: var(--charcoal);
            margin-bottom: 40px;
        }
        
        .form-group {
            margin-bottom: 30px;
        }
        
        label {
            display: block;
            margin-bottom: 12px;
            font-weight: 500;
            color: var(--charcoal);
        }
        
        input, textarea, select {
            width: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            font-family: 'Montserrat', sans-serif;
            background: rgba(249, 247, 245, 0.5);
            transition: var(--transition);
        }
        
        input:focus, textarea:focus, select:focus {
            outline: none;
            border-color: var(--gold);
            background: white;
        }
        
        textarea {
            height: 150px;
            resize: vertical;
        }
        
        .submit-btn {
            background: var(--gold);
            color: var(--charcoal);
            border: none;
            padding: 18px 45px;
            font-size: 0.9rem;
            cursor: pointer;
            transition: var(--transition);
            text-transform: uppercase;
            letter-spacing: 2px;
            font-weight: 500;
            width: 100%;
        }
        
        .submit-btn:hover {
            background: var(--charcoal);
            color: var(--gold);
        }
        
        /* Footer */
        footer {
            position: fixed;
            bottom: 0;
            right: 0;
            padding: 30px;
            z-index: 1000;
        }
        
        .social-links {
            display: flex;
            gap: 20px;
        }
        
        .social-link {
            color: var(--charcoal);
            font-size: 1.2rem;
            transition: var(--transition);
        }
        
        .social-link:hover {
            color: var(--gold);
            transform: translateY(-3px);
        }
        
        /* Responsive */
        @media (max-width: 1440px) {
            #about, #services {
                padding: 80px;
            }
            
            .contact-container {
                flex-direction: column;
            }
            
            .contact-info, .contact-form {
                padding: 60px;
            }
        }
        
        @media (max-width: 1200px) {
            nav {
                width: 80px;
                padding: 40px 0;
            }
            
            main {
                margin-left: 80px;
            }
            
            #about {
                flex-direction: column;
                gap: 60px;
            }
            
            .profile-image-container {
                flex: 0 0 auto;
                width: 100%;
                max-width: 500px;
            }
            
            .profile-image {
                height: auto;
            }
            
            .services-grid {
                grid-template-columns: 1fr 1fr;
            }
        }
        
        @media (max-width: 992px) {
            section {
                padding: 60px;
            }
            
            .hero-title {
                font-size: 3.5rem;
            }
            
            .stats-grid {
                grid-template-columns: 1fr 1fr;
            }
        }
        
        @media (max-width: 768px) {
            nav {
                width: 70px;
                padding: 30px 0;
            }
            
            .nav-logo {
                width: 50px;
                height: 50px;
                margin-bottom: 40px;
            }
            
            main {
                margin-left: 70px;
            }
            
            section {
                padding: 60px 40px;
            }
            
            .hero-title {
                font-size: 2.8rem;
            }
            
            .hero-subtitle {
                font-size: 1.1rem;
            }
            
            .section-title {
                font-size: 2.2rem;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .contact-info, .contact-form {
                padding: 40px;
            }
        }
        
        @media (max-width: 576px) {
            nav {
                width: 60px;
                padding: 20px 0;
            }
            
            .nav-menu {
                gap: 30px;
            }
            
            main {
                margin-left: 60px;
            }
            
            section {
                padding: 60px 30px;
            }
            
            .hero-title {
                font-size: 2.3rem;
            }
            
            .hero-text {
                font-size: 1rem;
            }
            
            .profile-image {
                box-shadow: 15px 15px 0 var(--gold);
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <img src="https://i.imgur.com/phZDA7w.jpeg" alt="ML Logo" class="nav-logo">
        <div class="nav-menu">
            <a href="#home" class="nav-item active">
                <i class="fas fa-home"></i>
                <span class="nav-label">Home</span>
            </a>
            <a href="#about" class="nav-item">
                <i class="fas fa-user"></i>
                <span class="nav-label">About</span>
            </a>
            <a href="#services" class="nav-item">
                <i class="fas fa-briefcase"></i>
                <span class="nav-label">Services</span>
            </a>
            <a href="#contact" class="nav-item">
                <i class="fas fa-envelope"></i>
                <span class="nav-label">Contact</span>
            </a>
        </div>
    </nav>

    <!-- Main Content -->
    <main>
        <!-- Home Section -->
        <section id="home">
            <div class="hero-content" data-aos="fade-up" data-aos-duration="1000">
                <h1 class="hero-title">Matthew Louis</h1>
                <p class="hero-subtitle">Luxury Real Estate Strategist</p>
                <p class="hero-text">
                    Transforming high-value properties into exceptional investments through 
                    data-driven strategies and bespoke management solutions. With a Wharton 
                    pedigree and European sensibility, I elevate real estate beyond 
                    conventional boundaries.
                </p>
                <a href="#contact" class="cta-button">Schedule Consultation</a>
                <div class="signature">ML</div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about">
            <div class="profile-image-container" data-aos="fade-right" data-aos-duration="1000">
                <img src="https://i.imgur.com/phZDA7w.jpeg" alt="Matthew Louis" class="profile-image">
            </div>
            <div class="about-content" data-aos="fade-left" data-aos-duration="1000" data-aos-delay="200">
                <h2 class="section-title">About Matthew</h2>
                <p class="about-text">
                    A <span class="highlight">French-American financier</span> with 17 years of transatlantic experience, 
                    I bridge the worlds of academic rigor and practical investment strategy. 
                    My Wharton PhD in Finance informs every aspect of my <span class="highlight">property 
                    optimization methodology</span>.
                </p>
                <p class="about-text">
                    After analyzing market behaviors at the highest levels, I discovered 
                    my true calling: <span class="highlight">redefining luxury hospitality investments</span>. 
                    My approach combines quantitative precision with an artful understanding 
                    of what discerning travelers truly desire.
                </p>
                <p class="about-text">
                    When not evaluating properties across three continents, I curate an 
                    exceptional Bordeaux collection and advise on rare wine investments - 
                    another passion where <span class="highlight">value meets virtuosity</span>.
                </p>
                
                <div class="stats-grid">
                    <div class="stat-item" data-aos="fade-up" data-aos-duration="800">
                        <div class="stat-number">17+</div>
                        <div class="stat-label">Years Experience</div>
                    </div>
                    <div class="stat-item" data-aos="fade-up" data-aos-duration="800" data-aos-delay="100">
                        <div class="stat-number">$42M</div>
                        <div class="stat-label">Assets Managed</div>
                    </div>
                    <div class="stat-item" data-aos="fade-up" data-aos-duration="800" data-aos-delay="200">
                        <div class="stat-number">92%</div>
                        <div class="stat-label">Occupancy Rate</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Services Section -->
        <section id="services">
            <div class="services-header" data-aos="fade-up" data-aos-duration="1000">
                <h2 class="section-title" style="color: var(--gold);">Services</h2>
                <p class="about-text" style="color: white; opacity: 0.8;">
                    Tailored solutions for discerning investors seeking premium returns in luxury real estate.
                </p>
            </div>
            <div class="services-grid">
                <div class="service-card" data-aos="fade-up" data-aos-duration="800">
                    <div class="service-icon"><i class="fas fa-chart-line"></i></div>
                    <h3 class="service-title">Investment Strategy</h3>
                    <p class="service-description">
                        Comprehensive market analysis and acquisition planning for luxury properties with highest yield potential. 
                        Our proprietary algorithms identify undervalued assets with 94% accuracy.
                    </p>
                </div>
                <div class="service-card" data-aos="fade-up" data-aos-duration="800" data-aos-delay="100">
                    <div class="service-icon"><i class="fas fa-home"></i></div>
                    <h3 class="service-title">Asset Optimization</h3>
                    <p class="service-description">
                        Revenue maximization through dynamic pricing, strategic positioning, and premium guest experiences. 
                        Average 28% increase in NOI within first year of implementation.
                    </p>
                </div>
                <div class="service-card" data-aos="fade-up" data-aos-duration="800" data-aos-delay="200">
                    <div class="service-icon"><i class="fas fa-concierge-bell"></i></div>
                    <h3 class="service-title">White-Glove Management</h3>
                    <p class="service-description">
                        Discreet, comprehensive property management maintaining asset value while delivering exceptional returns. 
                        24/7 concierge service with average response time under 12 minutes.
                    </p>
                </div>
                <div class="service-card" data-aos="fade-up" data-aos-duration="800" data-aos-delay="300">
                    <div class="service-icon"><i class="fas fa-handshake"></i></div>
                    <h3 class="service-title">Portfolio Diversification</h3>
                    <p class="service-description">
                        Strategic allocation across global luxury markets to mitigate risk and maximize returns. 
                        Access to exclusive off-market opportunities through our investor network.
                    </p>
                </div>
                <div class="service-card" data-aos="fade-up" data-aos-duration="800" data-aos-delay="400">
                    <div class="service-icon"><i class="fas fa-paint-roller"></i></div>
                    <h3 class="service-title">Design Curation</h3>
                    <p class="service-description">
                        Bespoke interior design services that increase property value and guest satisfaction. 
                        Collaborations with renowned designers and art consultants.
                    </p>
                </div>
                <div class="service-card" data-aos="fade-up" data-aos-duration="800" data-aos-delay="500">
                    <div class="service-icon"><i class="fas fa-globe"></i></div>
                    <h3 class="service-title">Global Network</h3>
                    <p class="service-description">
                        Leverage our international connections in key luxury markets including Paris, New York, 
                        Miami, London, and Dubai. Multilingual support team.
                    </p>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact">
            <div class="contact-container">
                <div class="contact-info" data-aos="fade-right" data-aos-duration="1000">
                    <h2 class="info-title">Get In Touch</h2>
                    <div class="info-item">
                        <div class="info-icon"><i class="fas fa-map-marker-alt"></i></div>
                        <div class="info-content">
                            <h3>Location</h3>
                            <p>New York | Paris | Miami</p>
                        </div>
                    </div>
                    <div class="info-item">
                        <div class="info-icon"><i class="fas fa-envelope"></i></div>
                        <div class="info-content">
                            <h3>Email</h3>
                            <a href="mailto:mlouis@luxe-estates.com">mlouis@luxe-estates.com</a>
                        </div>
                    </div>
                    <div class="info-item">
                        <div class="info-icon"><i class="fas fa-phone"></i></div>
                        <div class="info-content">
                            <h3>Phone</h3>
                            <a href="tel:+12125551234">+1 (212) 555-1234</a>
                        </div>
                    </div>
                    <div class="info-item">
                        <div class="info-icon"><i class="fas fa-clock"></i></div>
                        <div class="info-content">
                            <h3>Availability</h3>
                            <p>Mon-Fri: 9AM - 6PM EST<br>
                            By appointment only</p>
                        </div>
                    </div>
                </div>
                <div class="contact-form" data-aos="fade-left" data-aos-duration="1000">
                    <h2 class="form-title">Send Inquiry</h2>
                    <form id="inquiryForm">
                        <div class="form-group">
                            <label for="name">Full Name</label>
                            <input type="text" id="name" required>
                        </div>
                        <div class="form-group">
                            <label for="email">Email Address</label>
                            <input type="email" id="email" required>
                        </div>
                        <div class="form-group">
                            <label for="phone">Phone Number</label>
                            <input type="tel" id="phone">
                        </div>
                        <div class="form-group">
                            <label for="interest">Interest</label>
                            <select id="interest">
                                <option value="">Select an option</option>
                                <option value="investment">Investment Strategy</option>
                                <option value="management">Property Management</option>
                                <option value="acquisition">Property Acquisition</option>
                                <option value="other">Other</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="message">Message</label>
                            <textarea id="message" required></textarea>
                        </div>
                        <button type="submit" class="submit-btn">Submit Inquiry</button>
                    </form>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer data-aos="fade-left" data-aos-duration="1000" data-aos-anchor-placement="top-bottom">
        <div class="social-links">
            <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
            <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
            <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
        </div>
    </footer>

    <!-- AOS Animation -->
    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    
    <script>
        // Initialize AOS animation
        AOS.init({
            once: true,
            duration: 800,
            easing: 'ease-in-out-quart'
        });
        
        // Smooth scrolling for navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                document.querySelectorAll('.nav-item').forEach(item => {
                    item.classList.remove('active');
                });
                this.classList.add('active');
                
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
        
        // Update active nav item on scroll
        window.addEventListener('scroll', function() {
            let fromTop = window.scrollY;
            
            document.querySelectorAll('section').forEach(section => {
                let sectionTop = section.offsetTop;
                let sectionHeight = section.offsetHeight;
                let id = section.getAttribute('id');
                
                if (fromTop >= sectionTop - 200 && fromTop < sectionTop + sectionHeight - 200) {
                    document.querySelectorAll('.nav-item').forEach(item => {
                        item.classList.remove('active');
                        if (item.getAttribute('href') === `#${id}`) {
                            item.classList.add('active');
                        }
                    });
                }
            });
        });
        
        // Form submission
        document.getElementById('inquiryForm').addEventListener('submit', function(e) {
            e.preventDefault();
            // Here you would typically send the form data to your server
            alert('Thank you for your inquiry. We will contact you shortly.');
            this.reset();
        });
    </script>
</body>
</html>
