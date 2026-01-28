<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perfums — Розливна Парфумерія</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;600&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --black: #0a0a0a;
            --white: #fafafa;
            --gray: #6a6a6a;
            --light-gray: #e5e5e5;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background: var(--white);
            color: var(--black);
            overflow-x: hidden;
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            padding: 2rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(250, 250, 250, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            border-bottom: 1px solid var(--light-gray);
        }

        .logo {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2.5rem;
            font-weight: 300;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            position: relative;
        }

        .logo::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 1px;
            background: var(--black);
            transition: width 0.6s ease;
        }

        .logo:hover::after {
            width: 100%;
        }

        nav {
            display: flex;
            gap: 3rem;
        }

        nav a {
            color: var(--black);
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 300;
            letter-spacing: 0.1em;
            text-transform: uppercase;
            position: relative;
            transition: color 0.3s;
        }

        nav a::before {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 1px;
            background: var(--black);
            transition: width 0.4s ease;
        }

        nav a:hover::before {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            margin-top: 80px;
            overflow: hidden;
        }

        .hero-content {
            text-align: center;
            z-index: 2;
            animation: fadeInUp 1.2s ease-out;
        }

        .hero h1 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 6rem;
            font-weight: 300;
            letter-spacing: 0.2em;
            margin-bottom: 1rem;
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.1rem;
            letter-spacing: 0.15em;
            color: var(--gray);
            font-weight: 300;
            margin-bottom: 0.5rem;
        }

        .hero-origin {
            font-size: 0.95rem;
            letter-spacing: 0.2em;
            color: var(--black);
            font-weight: 400;
            margin-bottom: 3rem;
            text-transform: uppercase;
        }

        .cta-button {
            display: inline-block;
            padding: 1.2rem 3rem;
            background: var(--black);
            color: var(--white);
            text-decoration: none;
            font-size: 0.9rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            transition: all 0.4s ease;
            border: 2px solid var(--black);
            position: relative;
            overflow: hidden;
        }

        .cta-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: var(--white);
            transition: left 0.5s ease;
            z-index: -1;
        }

        .cta-button:hover::before {
            left: 0;
        }

        .cta-button:hover {
            color: var(--black);
        }

        .hero-bg {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 600px;
            height: 600px;
            border: 1px solid var(--light-gray);
            border-radius: 50%;
            opacity: 0.3;
            animation: pulse 8s ease-in-out infinite;
        }

        .hero-bg::before,
        .hero-bg::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            border: 1px solid var(--light-gray);
            border-radius: 50%;
        }

        .hero-bg::before {
            width: 450px;
            height: 450px;
        }

        .hero-bg::after {
            width: 300px;
            height: 300px;
        }

        /* Products Section */
        .products {
            padding: 8rem 5%;
            background: linear-gradient(to bottom, var(--white) 0%, #f5f5f5 100%);
        }

        .section-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 3.5rem;
            font-weight: 300;
            text-align: center;
            margin-bottom: 0.5rem;
            letter-spacing: 0.15em;
        }

        .section-subtitle {
            text-align: center;
            color: var(--gray);
            font-size: 1rem;
            letter-spacing: 0.1em;
            margin-bottom: 1rem;
            font-weight: 300;
        }

        .price-note {
            text-align: center;
            color: var(--black);
            font-size: 0.9rem;
            letter-spacing: 0.05em;
            margin-bottom: 5rem;
            font-weight: 400;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 3rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .product-card {
            background: var(--white);
            padding: 2.5rem;
            border: 1px solid var(--light-gray);
            transition: all 0.5s ease;
            position: relative;
            overflow: hidden;
        }

        .product-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: var(--black);
            transition: left 0.6s ease;
            z-index: 1;
        }

        .product-card:hover::before {
            left: 0;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15);
        }

        .product-card > * {
            position: relative;
            z-index: 2;
            transition: color 0.3s ease 0.2s;
        }

        .product-card:hover > * {
            color: var(--white);
        }

        .product-icon {
            width: 80px;
            height: 80px;
            margin: 0 auto 2rem;
            border: 2px solid var(--black);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Cormorant Garamond', serif;
            font-size: 2rem;
            font-weight: 600;
            transition: border-color 0.3s ease 0.2s;
        }

        .product-card:hover .product-icon {
            border-color: var(--white);
        }

        .product-name {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.8rem;
            margin-bottom: 0.5rem;
            text-align: center;
            font-weight: 400;
        }

        .product-volume {
            text-align: center;
            color: var(--gray);
            font-size: 0.9rem;
            margin-bottom: 1.5rem;
            letter-spacing: 0.1em;
            font-weight: 300;
        }

        .product-card:hover .product-volume {
            color: #c5c5c5;
        }

        .product-price {
            font-size: 1.5rem;
            text-align: center;
            font-weight: 500;
            letter-spacing: 0.05em;
        }

        .product-description {
            text-align: center;
            font-size: 0.85rem;
            color: var(--gray);
            margin-top: 1rem;
            line-height: 1.6;
            font-weight: 300;
        }

        .product-card:hover .product-description {
            color: #c5c5c5;
        }

        /* Features Section */
        .features {
            padding: 8rem 5%;
            background: var(--black);
            color: var(--white);
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 4rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .feature {
            text-align: center;
            animation: fadeInUp 0.8s ease-out;
        }

        .feature-icon {
            width: 60px;
            height: 60px;
            margin: 0 auto 1.5rem;
            border: 1px solid var(--white);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }

        .feature h3 {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.5rem;
            margin-bottom: 1rem;
            font-weight: 400;
            letter-spacing: 0.1em;
        }

        .feature p {
            color: #c5c5c5;
            font-size: 0.9rem;
            line-height: 1.8;
            font-weight: 300;
        }

        /* Footer */
        footer {
            padding: 4rem 5%;
            background: var(--white);
            border-top: 1px solid var(--light-gray);
            text-align: center;
        }

        .footer-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .footer-logo {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2rem;
            letter-spacing: 0.3em;
            margin-bottom: 2rem;
            font-weight: 300;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .footer-links a {
            color: var(--gray);
            text-decoration: none;
            font-size: 0.85rem;
            letter-spacing: 0.1em;
            transition: color 0.3s;
        }

        .footer-links a:hover {
            color: var(--black);
        }

        .copyright {
            color: var(--gray);
            font-size: 0.8rem;
            letter-spacing: 0.05em;
            font-weight: 300;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0%, 100% {
                transform: translate(-50%, -50%) scale(1);
                opacity: 0.3;
            }
            50% {
                transform: translate(-50%, -50%) scale(1.1);
                opacity: 0.15;
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 3.5rem;
            }

            .section-title {
                font-size: 2.5rem;
            }

            nav {
                gap: 1.5rem;
            }

            nav a {
                font-size: 0.75rem;
            }

            .product-grid {
                grid-template-columns: 1fr;
            }

            .features-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">Perfums</div>
        <nav>
            <a href="#products">Продукція</a>
            <a href="#about">Про нас</a>
            <a href="#contact">Контакти</a>
        </nav>
    </header>

    <section class="hero">
        <div class="hero-bg"></div>
        <div class="hero-content">
            <h1>PERFUMS</h1>
            <p>Розливна парфумерія преміум якості</p>
            <p class="hero-origin">Франція • Швейцарія</p>
            <a href="#products" class="cta-button">Переглянути колекцію</a>
        </div>
    </section>

    <section class="products" id="products">
        <h2 class="section-title">Наша Колекція</h2>
        <p class="section-subtitle">Обирайте ідеальний аромат для будь-якого моменту • Від 60 до 90 грн/мл</p>
        <p class="price-note">Ціна: від 60 до 90 грн за 1 мл</p>
        
        <div class="product-grid">
            <div class="product-card">
                <div class="product-icon">5</div>
                <h3 class="product-name">Пробник</h3>
                <p class="product-volume">5 мл</p>
                <div class="product-price">300-450 грн</div>
                <p class="product-description">Ідеальний вибір для знайомства з новим ароматом</p>
            </div>

            <div class="product-card">
                <div class="product-icon">10</div>
                <h3 class="product-name">Класик</h3>
                <p class="product-volume">10 мл</p>
                <div class="product-price">600-900 грн</div>
                <p class="product-description">Оптимальний об'єм для щоденного використання</p>
            </div>

            <div class="product-card">
                <div class="product-icon">15</div>
                <h3 class="product-name">Стандарт</h3>
                <p class="product-volume">15 мл</p>
                <div class="product-price">900-1350 грн</div>
                <p class="product-description">Популярний вибір наших клієнтів</p>
            </div>

            <div class="product-card">
                <div class="product-icon">20</div>
                <h3 class="product-name">Преміум</h3>
                <p class="product-volume">20 мл</p>
                <div class="product-price">1200-1800 грн</div>
                <p class="product-description">Максимальна вигода та тривалість аромату</p>
            </div>
        </div>
    </section>

    <section class="features" id="about">
        <div class="features-grid">
            <div class="feature">
                <div class="feature-icon">🇫🇷</div>
                <h3>Виробництво Франції та Швейцарії</h3>
                <p>Преміум парфумерія від провідних європейських виробників</p>
            </div>

            <div class="feature">
                <div class="feature-icon">◆</div>
                <h3>Оригінальні аромати</h3>
                <p>Працюємо лише з перевіреними постачальниками оригінальної парфумерії</p>
            </div>

            <div class="feature">
                <div class="feature-icon">✧</div>
                <h3>Широкий асортимент</h3>
                <p>Понад 200 ароматів від світових брендів у нашій колекції</p>
            </div>

            <div class="feature">
                <div class="feature-icon">◇</div>
                <h3>Швидка доставка</h3>
                <p>Відправляємо замовлення протягом 24 годин по всій Україні</p>
            </div>
        </div>
    </section>

    <footer id="contact">
        <div class="footer-content">
            <div class="footer-logo">PERFUMS</div>
            <div class="footer-links">
                <a href="https://www.instagram.com/my_perfums1?igsh=ZndlcTdnYmJqMGRv" target="_blank">Instagram</a>
                <a href="https://www.facebook.com/profile.php?id=61584438068464" target="_blank">Facebook</a>
                <a href="https://t.me/valiabaiurak" target="_blank">Telegram</a>
            </div>
            <p class="copyright">© 2026 Perfums. Всі права захищені.</p>
        </div>
    </footer>

    <script>
        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Animate features on scroll
        const observerOptions = {
            threshold: 0.2,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry, index) => {
                if (entry.isIntersecting) {
                    setTimeout(() => {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }, index * 100);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.feature').forEach(feature => {
            feature.style.opacity = '0';
            feature.style.transform = 'translateY(20px)';
            feature.style.transition = 'all 0.6s ease';
            observer.observe(feature);
        });

        // Product cards stagger animation
        document.querySelectorAll('.product-card').forEach((card, index) => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(30px)';
            card.style.transition = 'all 0.6s ease';
            
            setTimeout(() => {
                card.style.opacity = '1';
                card.style.transform = 'translateY(0)';
            }, 200 + (index * 150));
        });
    </script>
</body>
</html>
