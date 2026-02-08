<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PERFUMS — Розливна Парфумерія</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;600;700&family=Montserrat:wght@300;400;500;600&family=Playfair+Display:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --black: #0a0a0a;
            --white: #fafafa;
            --gray: #6a6a6a;
            --light-gray: #e5e5e5;
            --accent: #7b8fa3;
            --dark-accent: #5b6f83;
            --light-accent: #9badbd;
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

        /* Animated Background Particles */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            opacity: 0.05;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: var(--black);
            border-radius: 50%;
            animation: float 20s infinite;
        }

        @keyframes float {
            0%, 100% {
                transform: translate(0, 0) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.3;
            }
            90% {
                opacity: 0.3;
            }
            100% {
                transform: translate(100px, -100vh) rotate(360deg);
                opacity: 0;
            }
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
            background: rgba(250, 250, 250, 0.98);
            backdrop-filter: blur(20px);
            z-index: 1000;
            border-bottom: 1px solid transparent;
            transition: all 0.3s ease;
        }

        header.scrolled {
            padding: 1.2rem 5%;
            border-bottom: 1px solid var(--light-gray);
            box-shadow: 0 5px 30px rgba(0, 0, 0, 0.05);
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            font-weight: 700;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            position: relative;
            background: linear-gradient(135deg, var(--black) 0%, var(--gray) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .logo::before {
            content: 'PERFUMS';
            position: absolute;
            top: 0;
            left: 0;
            background: linear-gradient(135deg, var(--accent) 0%, var(--dark-accent) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .logo:hover::before {
            opacity: 1;
        }

        nav {
            display: flex;
            gap: 3rem;
        }

        .menu-toggle {
            display: none;
            flex-direction: column;
            gap: 6px;
            cursor: pointer;
            padding: 8px;
            z-index: 1001;
        }

        .menu-toggle span {
            width: 28px;
            height: 2px;
            background: var(--black);
            transition: all 0.3s ease;
            border-radius: 2px;
        }

        .menu-toggle.active span:nth-child(1) {
            transform: rotate(45deg) translate(8px, 8px);
        }

        .menu-toggle.active span:nth-child(2) {
            opacity: 0;
        }

        .menu-toggle.active span:nth-child(3) {
            transform: rotate(-45deg) translate(8px, -8px);
        }

        @media (max-width: 768px) {
            .menu-toggle {
                display: flex;
            }

            nav {
                position: fixed;
                top: 0;
                right: -100%;
                width: 70%;
                height: 100vh;
                background: rgba(250, 250, 250, 0.98);
                backdrop-filter: blur(20px);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                gap: 2.5rem;
                transition: right 0.5s cubic-bezier(0.4, 0, 0.2, 1);
                box-shadow: -5px 0 30px rgba(0, 0, 0, 0.1);
                z-index: 999;
            }

            nav.active {
                right: 0;
            }

            nav a {
                font-size: 1.2rem;
                padding: 1rem;
            }
        }

        nav a {
            color: var(--black);
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 400;
            letter-spacing: 0.1em;
            text-transform: uppercase;
            position: relative;
            transition: all 0.3s;
        }

        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 50%;
            transform: translateX(-50%) scaleX(0);
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent), transparent);
            transition: transform 0.4s ease;
        }

        nav a:hover {
            color: var(--accent);
        }

        nav a:hover::after {
            transform: translateX(-50%) scaleX(1);
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            margin-top: 80px;
            overflow: hidden;
            background: linear-gradient(135deg, #fafafa 0%, #f0f0f0 50%, #e8e8e8 100%);
        }

        .hero-bg-gradient {
            position: absolute;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(123, 143, 163, 0.03) 0%, transparent 50%),
                radial-gradient(circle at 80% 50%, rgba(10, 10, 10, 0.03) 0%, transparent 50%);
            animation: gradientShift 15s ease infinite;
        }

        @keyframes gradientShift {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .hero-content {
            text-align: center;
            z-index: 2;
            animation: fadeInUp 1.5s ease-out;
            position: relative;
        }

        .hero h1 {
            font-family: 'Playfair Display', serif;
            font-size: 8rem;
            font-weight: 700;
            letter-spacing: 0.25em;
            margin-bottom: 1rem;
            line-height: 1.1;
            background: linear-gradient(135deg, var(--black) 0%, var(--gray) 50%, var(--black) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            background-size: 200% 200%;
            animation: gradientMove 8s ease infinite;
        }

        @keyframes gradientMove {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .hero-subtitle {
            font-size: 1.3rem;
            letter-spacing: 0.2em;
            color: var(--gray);
            font-weight: 300;
            margin-bottom: 1.5rem;
            opacity: 0;
            animation: fadeIn 1s ease 0.5s forwards;
        }

        .hero-origin {
            font-size: 1rem;
            letter-spacing: 0.2em;
            color: var(--black);
            font-weight: 500;
            margin: 0 auto 3rem;
            text-transform: uppercase;
            opacity: 0;
            animation: fadeIn 1s ease 0.8s forwards;
            position: relative;
            display: inline-flex;
            align-items: center;
            gap: 1.5rem;
            padding: 1.2rem 3rem;
            background: linear-gradient(135deg, rgba(255,255,255,0.95), rgba(245,245,245,0.85));
            border: 2px solid var(--light-gray);
            border-radius: 50px;
            backdrop-filter: blur(10px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            transition: all 0.4s ease;
        }

        .hero-origin:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.12);
            border-color: var(--accent);
        }

        .country-flag {
            font-size: 2rem;
            animation: floatFlag 3s ease-in-out infinite;
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.1));
        }

        .country-flag:first-child {
            animation-delay: 0s;
        }

        .country-flag:last-child {
            animation-delay: 1.5s;
        }

        @keyframes floatFlag {
            0%, 100% {
                transform: translateY(0px) scale(1);
            }
            50% {
                transform: translateY(-5px) scale(1.05);
            }
        }

        .origin-divider {
            width: 2px;
            height: 24px;
            background: linear-gradient(180deg, transparent, var(--accent), transparent);
        }

        .cta-button {
            display: inline-block;
            padding: 1.5rem 4rem;
            background: var(--black);
            color: var(--white);
            text-decoration: none;
            font-size: 0.95rem;
            letter-spacing: 0.25em;
            text-transform: uppercase;
            font-weight: 500;
            transition: all 0.5s ease;
            border: 2px solid var(--black);
            position: relative;
            overflow: hidden;
            opacity: 0;
            animation: fadeIn 1s ease 1.1s forwards;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .cta-button::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent), var(--dark-accent));
            transition: width 0.6s ease, height 0.6s ease;
            transform: translate(-50%, -50%);
            z-index: 0;
        }

        .cta-button:hover::before {
            width: 400px;
            height: 400px;
        }

        .cta-button span {
            position: relative;
            z-index: 1;
        }

        .cta-button:hover {
            border-color: var(--accent);
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(123, 143, 163, 0.3);
        }

        /* Decorative circles */
        .hero-circle {
            position: absolute;
            border: 1px solid var(--light-gray);
            border-radius: 50%;
            animation: rotate 30s linear infinite;
        }

        .hero-circle-1 {
            width: 800px;
            height: 800px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            opacity: 0.3;
        }

        .hero-circle-2 {
            width: 600px;
            height: 600px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            opacity: 0.2;
            animation-duration: 40s;
            animation-direction: reverse;
        }

        .hero-circle-3 {
            width: 400px;
            height: 400px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            opacity: 0.15;
        }

        @keyframes rotate {
            from { transform: translate(-50%, -50%) rotate(0deg); }
            to { transform: translate(-50%, -50%) rotate(360deg); }
        }

        /* Products Section */
        .products {
            padding: 10rem 5%;
            background: var(--white);
            position: relative;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 4.5rem;
            font-weight: 700;
            text-align: center;
            margin-bottom: 1rem;
            letter-spacing: 0.15em;
            background: linear-gradient(135deg, var(--black), var(--gray));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .section-subtitle {
            text-align: center;
            color: var(--gray);
            font-size: 1.1rem;
            letter-spacing: 0.1em;
            margin-bottom: 1.5rem;
            font-weight: 300;
        }

        .price-note {
            text-align: center;
            margin-bottom: 6rem;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 2rem;
        }

        .price-badge {
            background: linear-gradient(135deg, rgba(123, 143, 163, 0.1), rgba(123, 143, 163, 0.05));
            border: 2px solid var(--light-gray);
            padding: 1.2rem 3rem;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 500;
            letter-spacing: 0.15em;
            color: var(--black);
            position: relative;
            overflow: hidden;
            transition: all 0.4s ease;
        }

        .price-badge::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(123, 143, 163, 0.1), transparent);
            transition: left 0.6s ease;
        }

        .price-badge:hover::before {
            left: 100%;
        }

        .price-badge:hover {
            border-color: var(--accent);
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(123, 143, 163, 0.2);
        }

        .price-amount {
            color: var(--accent);
            font-weight: 600;
            font-size: 1.2rem;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 3rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .product-card {
            background: linear-gradient(135deg, #ffffff 0%, #f8f8f8 100%);
            padding: 3rem 2.5rem;
            border: 2px solid var(--light-gray);
            transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .product-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(135deg, 
                transparent 0%, 
                rgba(123, 143, 163, 0.05) 50%, 
                transparent 100%);
            transform: rotate(45deg);
            transition: all 0.8s ease;
        }

        .product-card:hover::before {
            left: 100%;
            top: 100%;
        }

        .product-card::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--black) 0%, #2a2a2a 100%);
            transform: scaleY(0);
            transform-origin: bottom;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 1;
        }

        .product-card:hover::after {
            transform: scaleY(1);
            transform-origin: top;
        }

        .product-card > * {
            position: relative;
            z-index: 2;
            transition: all 0.5s ease;
        }

        .product-card:hover {
            border-color: var(--accent);
            transform: translateY(-10px) scale(1.02);
            box-shadow: 
                0 20px 60px rgba(0, 0, 0, 0.15),
                0 0 0 1px var(--accent);
        }

        .product-card:hover > * {
            color: var(--white);
        }

        .product-icon {
            text-align: center;
            margin-bottom: 2rem;
            transform: scale(1);
            transition: transform 0.6s ease;
        }

        .product-card:hover .product-icon {
            transform: scale(1.1) translateY(-5px);
        }

        .product-icon svg {
            width: 80px;
            height: 100px;
            stroke: var(--black);
            transition: all 0.5s ease;
            filter: drop-shadow(0 5px 15px rgba(0, 0, 0, 0.1));
        }

        .product-card:hover .product-icon svg {
            stroke: var(--accent);
            filter: drop-shadow(0 10px 30px rgba(123, 143, 163, 0.5));
        }

        .product-name {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            text-align: center;
            margin-bottom: 0.5rem;
            font-weight: 600;
            letter-spacing: 0.15em;
        }

        .product-volume {
            text-align: center;
            color: var(--gray);
            font-size: 1rem;
            margin-bottom: 1.5rem;
            letter-spacing: 0.2em;
            font-weight: 400;
        }

        .product-card:hover .product-volume {
            color: var(--light-gray);
        }

        .product-price {
            text-align: center;
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            font-weight: 600;
            letter-spacing: 0.1em;
            color: var(--accent);
        }

        .product-card:hover .product-price {
            color: var(--light-accent);
        }

        .product-description {
            text-align: center;
            font-size: 0.9rem;
            line-height: 1.8;
            color: var(--gray);
            font-weight: 300;
        }

        .product-card:hover .product-description {
            color: #c5c5c5;
        }

        /* Fragrances Section */
        .fragrances {
            padding: 10rem 5%;
            background: linear-gradient(180deg, var(--white) 0%, #f5f5f5 100%);
            position: relative;
        }

        .gender-section {
            margin-bottom: 8rem;
        }

        .gender-title {
            font-family: 'Playfair Display', serif;
            font-size: 3.5rem;
            font-weight: 700;
            text-align: center;
            margin-bottom: 5rem;
            letter-spacing: 0.2em;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1.5rem;
            position: relative;
        }

        .gender-title::before,
        .gender-title::after {
            content: '';
            width: 100px;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent), transparent);
        }

        .gender-title svg {
            width: 35px;
            height: 35px;
            stroke: var(--accent);
            animation: pulse 2s ease infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .category-section {
            margin-bottom: 5rem;
            max-width: 1400px;
            margin-left: auto;
            margin-right: auto;
            background: var(--white);
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.05);
            transition: all 0.4s ease;
        }

        .category-section:hover {
            box-shadow: 0 15px 60px rgba(0, 0, 0, 0.1);
            transform: translateY(-5px);
        }

        .category-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 0;
            border-bottom: 2px solid var(--light-gray);
            margin-bottom: 3rem;
            position: relative;
        }

        .category-header::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.6s ease;
        }

        .category-section:hover .category-header::after {
            width: 100%;
        }

        .category-name {
            font-family: 'Playfair Display', serif;
            font-size: 2.2rem;
            font-weight: 600;
            letter-spacing: 0.1em;
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .category-name svg {
            width: 30px;
            height: 30px;
            stroke: var(--accent);
        }

        .category-price {
            font-size: 1rem;
            color: var(--gray);
            letter-spacing: 0.15em;
            font-weight: 500;
            padding: 0.8rem 1.5rem;
            background: linear-gradient(135deg, #f8f8f8, #f0f0f0);
            border-radius: 25px;
            border: 1px solid var(--light-gray);
        }

        .fragrance-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }

        .fragrance-item {
            padding: 2rem;
            border: 1px solid var(--light-gray);
            background: linear-gradient(135deg, #ffffff, #fafafa);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            text-align: center;
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .fragrance-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, 
                transparent, 
                rgba(123, 143, 163, 0.1), 
                transparent);
            transition: left 0.6s ease;
        }

        .fragrance-item:hover::before {
            left: 100%;
        }

        .fragrance-item:hover {
            border-color: var(--accent);
            transform: translateY(-5px) scale(1.03);
            box-shadow: 
                0 15px 40px rgba(0, 0, 0, 0.1),
                0 0 0 1px var(--accent);
            background: linear-gradient(135deg, #ffffff, #fcfcfc);
        }

        .fragrance-name {
            font-size: 1.05rem;
            font-weight: 500;
            letter-spacing: 0.08em;
            position: relative;
            z-index: 1;
            transition: color 0.3s ease;
        }

        .fragrance-item:hover .fragrance-name {
            color: var(--accent);
            font-weight: 600;
        }

        /* Features */
        .features {
            padding: 10rem 5%;
            background: linear-gradient(135deg, var(--black) 0%, #1a1a1a 100%);
            color: var(--white);
            position: relative;
            overflow: hidden;
        }

        .features::before {
            content: '';
            position: absolute;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(123, 143, 163, 0.1) 0%, transparent 70%);
            top: -250px;
            right: -250px;
            animation: floatFeature 20s ease infinite;
        }

        .features::after {
            content: '';
            position: absolute;
            width: 400px;
            height: 400px;
            background: radial-gradient(circle, rgba(123, 143, 163, 0.08) 0%, transparent 70%);
            bottom: -200px;
            left: -200px;
            animation: floatFeature 15s ease infinite reverse;
        }

        @keyframes floatFeature {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(30px, 30px); }
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 4rem;
            max-width: 1400px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        .feature {
            text-align: center;
            padding: 2rem;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            transition: all 0.5s ease;
            position: relative;
            overflow: hidden;
        }

        .feature::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, 
                transparent 0%, 
                rgba(123, 143, 163, 0.1) 50%, 
                transparent 100%);
            transform: translateX(-100%);
            transition: transform 0.6s ease;
        }

        .feature:hover::before {
            transform: translateX(100%);
        }

        .feature:hover {
            border-color: var(--accent);
            background: rgba(255, 255, 255, 0.05);
            transform: translateY(-10px);
            box-shadow: 0 20px 60px rgba(123, 143, 163, 0.2);
        }

        .feature-icon {
            width: 80px;
            height: 80px;
            margin: 0 auto 2rem;
            border: 2px solid var(--accent);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.5s ease;
            position: relative;
        }

        .feature:hover .feature-icon {
            transform: scale(1.1) rotate(360deg);
            box-shadow: 0 0 30px rgba(123, 143, 163, 0.5);
        }

        .feature-icon svg {
            width: 35px;
            height: 35px;
            stroke: var(--accent);
        }

        .feature h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.6rem;
            margin-bottom: 1.5rem;
            font-weight: 600;
            letter-spacing: 0.1em;
        }

        .feature p {
            color: #c5c5c5;
            font-size: 0.95rem;
            line-height: 1.9;
            font-weight: 300;
        }

        /* Footer */
        footer {
            padding: 5rem 5%;
            background: var(--white);
            border-top: 1px solid var(--light-gray);
            text-align: center;
            position: relative;
        }

        .footer-content {
            max-width: 900px;
            margin: 0 auto;
        }

        .footer-logo {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            letter-spacing: 0.3em;
            margin-bottom: 3rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--black), var(--gray));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }

        .social-link {
            display: inline-flex;
            align-items: center;
            gap: 1rem;
            color: var(--black);
            text-decoration: none;
            font-size: 0.9rem;
            letter-spacing: 0.15em;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            padding: 1.2rem 2rem;
            border: 2px solid var(--light-gray);
            position: relative;
            overflow: hidden;
            font-weight: 500;
        }

        .social-link::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: linear-gradient(135deg, var(--black), #2a2a2a);
            transform: translate(-50%, -50%);
            border-radius: 50%;
            transition: width 0.6s ease, height 0.6s ease;
            z-index: 0;
        }

        .social-link:hover::before {
            width: 400px;
            height: 400px;
        }

        .social-link span,
        .social-link svg {
            position: relative;
            z-index: 1;
            transition: all 0.5s ease;
        }

        .social-link:hover {
            border-color: var(--accent);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
        }

        .social-link:hover span,
        .social-link:hover svg {
            color: var(--white);
            stroke: var(--accent);
        }

        .social-link svg {
            width: 22px;
            height: 22px;
            stroke: var(--black);
        }

        .copyright {
            color: var(--gray);
            font-size: 0.85rem;
            letter-spacing: 0.1em;
            font-weight: 300;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Responsive */
        @media (max-width: 1024px) {
            .hero h1 {
                font-size: 5rem;
            }

            .section-title {
                font-size: 3.5rem;
            }
        }

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 3.5rem;
                letter-spacing: 0.15em;
            }

            .section-title {
                font-size: 2.5rem;
            }

            .gender-title {
                font-size: 2.2rem;
                flex-direction: column;
            }

            .gender-title::before,
            .gender-title::after {
                width: 50px;
            }

            nav {
                gap: 1.5rem;
            }

            nav a {
                font-size: 0.75rem;
            }

            .product-grid,
            .features-grid,
            .fragrance-list {
                grid-template-columns: 1fr;
            }

            .category-header {
                flex-direction: column;
                gap: 1rem;
                align-items: flex-start;
            }

            .social-links {
                flex-direction: column;
                align-items: center;
            }

            .category-section {
                padding: 2rem 1.5rem;
            }

            .hero-origin {
                font-size: 0.85rem;
                padding: 1rem 2rem;
                gap: 1rem;
            }

            .country-flag {
                font-size: 1.5rem;
            }
        }

        /* Scroll Progress Bar */
        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            width: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--accent), var(--dark-accent));
            z-index: 10000;
            transition: width 0.1s ease;
        }
    </style>
</head>
<body>
    <!-- Scroll Progress Bar -->
    <div class="scroll-progress" id="scrollProgress"></div>

    <!-- Animated Particles -->
    <div class="particles" id="particles"></div>

    <header id="header">
        <div class="logo">PERFUMS</div>
        <div class="menu-toggle" id="menuToggle">
            <span></span>
            <span></span>
            <span></span>
        </div>
        <nav id="nav">
            <a href="#volumes">Об'єми</a>
            <a href="#fragrances">Аромати</a>
            <a href="#about">Про нас</a>
            <a href="#contact">Контакти</a>
        </nav>
    </header>

    <section class="hero">
        <div class="hero-bg-gradient"></div>
        <div class="hero-circle hero-circle-1"></div>
        <div class="hero-circle hero-circle-2"></div>
        <div class="hero-circle hero-circle-3"></div>
        <div class="hero-content">
            <h1>PERFUMS</h1>
            <p class="hero-subtitle">Розливна парфумерія преміум якості</p>
            <div class="hero-origin">
                <span class="country-flag">🇨🇭</span>
                <span>Швейцарія</span>
                <div class="origin-divider"></div>
                <span>Франція</span>
                <span class="country-flag">🇫🇷</span>
            </div>
            <a href="#volumes" class="cta-button"><span>Переглянути колекцію</span></a>
        </div>
    </section>

    <section class="products" id="volumes">
        <h2 class="section-title">Доступні Об'єми</h2>
        <p class="section-subtitle">Оберіть ідеальний розмір для вашого улюбленого аромату</p>
        <div class="price-note">
            <div class="price-badge">
                Ціна за 1 мл: <span class="price-amount">60-95 грн</span>
            </div>
        </div>
        
        <div class="product-grid">
            <div class="product-card">
                <div class="product-icon">
                    <svg viewBox="0 0 60 80" xmlns="http://www.w3.org/2000/svg" fill="none">
                        <rect x="15" y="15" width="30" height="50" stroke-width="2"/>
                        <rect x="20" y="5" width="20" height="12" stroke-width="2"/>
                        <line x1="25" y1="10" x2="35" y2="10" stroke-width="2"/>
                    </svg>
                </div>
                <h3 class="product-name">Пробник</h3>
                <p class="product-volume">5 МЛ</p>
                <div class="product-price">300-475 грн</div>
                <p class="product-description">Ідеальний вибір для знайомства з новим ароматом</p>
            </div>

            <div class="product-card">
                <div class="product-icon">
                    <svg viewBox="0 0 60 80" xmlns="http://www.w3.org/2000/svg" fill="none">
                        <rect x="12" y="12" width="36" height="56" stroke-width="2"/>
                        <rect x="18" y="3" width="24" height="12" stroke-width="2"/>
                        <circle cx="30" cy="9" r="2" fill="currentColor"/>
                    </svg>
                </div>
                <h3 class="product-name">Класик</h3>
                <p class="product-volume">10 МЛ</p>
                <div class="product-price">600-950 грн</div>
                <p class="product-description">Оптимальний об'єм для щоденного використання</p>
            </div>

            <div class="product-card">
                <div class="product-icon">
                    <svg viewBox="0 0 60 80" xmlns="http://www.w3.org/2000/svg" fill="none">
                        <rect x="10" y="10" width="40" height="60" stroke-width="2"/>
                        <rect x="16" y="2" width="28" height="11" stroke-width="2"/>
                        <rect x="22" y="4" width="16" height="3" fill="currentColor"/>
                    </svg>
                </div>
                <h3 class="product-name">Стандарт</h3>
                <p class="product-volume">15 МЛ</p>
                <div class="product-price">900-1425 грн</div>
                <p class="product-description">Популярний вибір наших клієнтів</p>
            </div>

            <div class="product-card">
                <div class="product-icon">
                    <svg viewBox="0 0 60 80" xmlns="http://www.w3.org/2000/svg" fill="none">
                        <rect x="8" y="8" width="44" height="64" stroke-width="2"/>
                        <rect x="14" y="1" width="32" height="10" stroke-width="2"/>
                        <circle cx="30" cy="6" r="3" fill="currentColor"/>
                        <line x1="20" y1="35" x2="40" y2="35" stroke-width="1.5"/>
                    </svg>
                </div>
                <h3 class="product-name">Преміум</h3>
                <p class="product-volume">20 МЛ</p>
                <div class="product-price">1200-1900 грн</div>
                <p class="product-description">Максимальна вигода та тривалість аромату</p>
            </div>
        </div>
    </section>

    <section class="fragrances" id="fragrances">
        <div class="gender-section">
            <h2 class="gender-title">
                <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="12" cy="9" r="5" stroke-width="2"/>
                    <line x1="12" y1="14" x2="12" y2="22" stroke-width="2"/>
                    <line x1="8" y1="18" x2="16" y2="18" stroke-width="2"/>
                </svg>
                Жіночі Аромати
            </h2>

            <!-- Квітково-фруктові -->
            <div class="category-section">
                <div class="category-header">
                    <h3 class="category-name">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M12 2C12 2 8 5 8 9C8 11.21 9.79 13 12 13C14.21 13 16 11.21 16 9C16 5 12 2 12 2Z" stroke-width="2"/>
                            <path d="M12 13V22" stroke-width="2"/>
                            <path d="M8 17C8 17 6 18 6 20C6 21.1 6.9 22 8 22" stroke-width="2"/>
                            <path d="M16 17C16 17 18 18 18 20C18 21.1 17.1 22 16 22" stroke-width="2"/>
                        </svg>
                        Квітково-фруктові
                    </h3>
                    <div class="category-price">60-75 грн/мл</div>
                </div>
                <div class="fragrance-list">
                    <div class="fragrance-item"><div class="fragrance-name">Tizianna Terenzi "Casiopea"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Mango-Skin</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Arman Basi in Red</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Victoria Secret Tease</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Zara "Cherry Watermelon"</div></div>
                </div>
            </div>

            <!-- Цитрусові -->
            <div class="category-section">
                <div class="category-header">
                    <h3 class="category-name">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="12" cy="12" r="8" stroke-width="2"/>
                            <path d="M12 4V12L16 16" stroke-width="2"/>
                            <circle cx="12" cy="12" r="2" fill="currentColor"/>
                        </svg>
                        Цитрусові
                    </h3>
                    <div class="category-price">65-80 грн/мл</div>
                </div>
                <div class="fragrance-list">
                    <div class="fragrance-item"><div class="fragrance-name">Dolche & Gabana "Light Blue"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Moschino Toy 2</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Blue Talisman</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Scandal "Pour Homme"</div></div>
                </div>
            </div>

            <!-- Свіжі -->
            <div class="category-section">
                <div class="category-header">
                    <h3 class="category-name">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M9.59 4.59A2 2 0 1 1 11 8H2m10.59 11.41A2 2 0 1 0 14 16H2m15.73-8.27A2.5 2.5 0 1 1 19.5 12H2" stroke-width="2" stroke-linecap="round"/>
                        </svg>
                        Свіжі
                    </h3>
                    <div class="category-price">70-80 грн/мл</div>
                </div>
                <div class="fragrance-list">
                    <div class="fragrance-item"><div class="fragrance-name">Chanel "Chance Fraiche"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Dunhill "Desire Blue"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Kenzo "Pour Homme"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Chanel "Amour Amoser"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Dolche & Gabana "Blue"</div></div>
                </div>
            </div>

            <!-- Східні деревно-квіткові -->
            <div class="category-section">
                <div class="category-header">
                    <h3 class="category-name">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M12 2L15.09 8.26L22 9.27L17 14.14L18.18 21.02L12 17.77L5.82 21.02L7 14.14L2 9.27L8.91 8.26L12 2Z" stroke-width="2"/>
                        </svg>
                        Східні деревно-квіткові
                    </h3>
                    <div class="category-price">75-90 грн/мл</div>
                </div>
                <div class="fragrance-list">
                    <div class="fragrance-item"><div class="fragrance-name">Tom Ford "Lost Cherry"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Calvin Klein "Euphoria"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Givenchy "Angel & Demon"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Armani "My Way"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Versace Versense</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Lacoste "Hot Day"</div></div>
                </div>
            </div>

            <!-- Східні пряно-деревні -->
            <div class="category-section">
                <div class="category-header">
                    <h3 class="category-name">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M8.5 14.5A2.5 2.5 0 0 0 11 12c0-1.38-.5-2-1-3-1.072-2.143-.224-4.054 2-6 .5 2.5 2 4.9 4 6.5 2 1.6 3 3.5 3 5.5a7 7 0 1 1-14 0c0-1.153.433-2.294 1-3a2.5 2.5 0 0 0 2.5 2.5z" stroke-width="2"/>
                        </svg>
                        Східні пряно-деревні
                    </h3>
                    <div class="category-price">80-95 грн/мл</div>
                </div>
                <div class="fragrance-list">
                    <div class="fragrance-item"><div class="fragrance-name">Tom Ford "Smoking"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Tom Ford Vanilla</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Atari Collection "Azalea"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Kilian "Smoking Hot"</div></div>
                </div>
            </div>
        </div>

        <!-- Чоловічі аромати -->
        <div class="gender-section">
            <h2 class="gender-title">
                <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="10" cy="14" r="6" stroke-width="2"/>
                    <line x1="14.5" y1="9.5" x2="21" y2="3" stroke-width="2"/>
                    <line x1="21" y1="3" x2="21" y2="7" stroke-width="2"/>
                    <line x1="21" y1="3" x2="17" y2="3" stroke-width="2"/>
                </svg>
                Чоловічі Аромати
            </h2>

            <!-- Деревні -->
            <div class="category-section">
                <div class="category-header">
                    <h3 class="category-name">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M12 2v20m0-20a4 4 0 014 4v2a2 2 0 002 2 2 2 0 01-2 2v2a4 4 0 01-4 4m0-16a4 4 0 00-4 4v2a2 2 0 01-2 2 2 2 0 002 2v2a4 4 0 004 4" stroke-width="2"/>
                        </svg>
                        Деревні
                    </h3>
                    <div class="category-price">75-95 грн/мл</div>
                </div>
                <div class="fragrance-list">
                    <div class="fragrance-item"><div class="fragrance-name">Savage</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Versace</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Creed Aventus</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Givenchy "Pour Homme"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Nasomatto "Black Afgano"</div></div>
                </div>
            </div>

            <!-- Цитрусові -->
            <div class="category-section">
                <div class="category-header">
                    <h3 class="category-name">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="12" cy="12" r="9" stroke-width="2"/>
                            <path d="M12 3v18M3 12h18" stroke-width="2"/>
                            <path d="M6 6l12 12M18 6L6 18" stroke-width="1" opacity="0.5"/>
                        </svg>
                        Цитрусові
                    </h3>
                    <div class="category-price">80-95 грн/мл</div>
                </div>
                <div class="fragrance-list">
                    <div class="fragrance-item"><div class="fragrance-name">Antonio Banderas "Blue"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Dolche & Gabana "Blue Man"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Paco Rabanne "Invictus"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Dolche & Gabana "The One Man"</div></div>
                    <div class="fragrance-item"><div class="fragrance-name">Kurdistan "L'Homme Base"</div></div>
                </div>
            </div>
        </div>
    </section>

    <section class="features" id="about">
        <div class="features-grid">
            <div class="feature">
                <div class="feature-icon">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M12 2L2 7L12 12L22 7L12 2Z" stroke-width="2"/>
                        <path d="M2 17L12 22L22 17" stroke-width="2"/>
                        <path d="M2 12L12 17L22 12" stroke-width="2"/>
                    </svg>
                </div>
                <h3>Виробництво Франції та Швейцарії</h3>
                <p>Преміум парфумерія від провідних європейських виробників</p>
            </div>

            <div class="feature">
                <div class="feature-icon">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M9 11l3 3L22 4" stroke-width="2" stroke-linecap="round"/>
                        <path d="M21 12v7a2 2 0 01-2 2H5a2 2 0 01-2-2V5a2 2 0 012-2h11" stroke-width="2"/>
                    </svg>
                </div>
                <h3>Оригінальні аромати</h3>
                <p>Працюємо лише з перевіреними постачальниками оригінальної парфумерії</p>
            </div>

            <div class="feature">
                <div class="feature-icon">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <rect x="3" y="3" width="7" height="7" stroke-width="2"/>
                        <rect x="14" y="3" width="7" height="7" stroke-width="2"/>
                        <rect x="14" y="14" width="7" height="7" stroke-width="2"/>
                        <rect x="3" y="14" width="7" height="7" stroke-width="2"/>
                    </svg>
                </div>
                <h3>Широкий асортимент</h3>
                <p>Понад 200 ароматів від світових брендів у нашій колекції</p>
            </div>

            <div class="feature">
                <div class="feature-icon">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <rect x="1" y="3" width="15" height="13" stroke-width="2"/>
                        <path d="M16 8l6-5v18l-6-5" stroke-width="2"/>
                    </svg>
                </div>
                <h3>Швидка доставка</h3>
                <p>Відправляємо замовлення протягом 24 годин по всій Україні</p>
            </div>
        </div>
    </section>

    <footer id="contact">
        <div class="footer-content">
            <div class="footer-logo">PERFUMS</div>
            <div class="social-links">
                <a href="https://www.instagram.com/my_perfums1?igsh=ZndlcTdnYmJqMGRv" target="_blank" class="social-link">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <rect x="2" y="2" width="20" height="20" rx="5" stroke-width="2"/>
                        <circle cx="12" cy="12" r="4" stroke-width="2"/>
                        <circle cx="18" cy="6" r="1.5" fill="currentColor"/>
                    </svg>
                    <span>Instagram</span>
                </a>
                <a href="https://www.facebook.com/profile.php?id=61584438068464" target="_blank" class="social-link">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <span>Facebook</span>
                </a>
                <a href="https://t.me/valiabaiurak" target="_blank" class="social-link">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M21.198 3.698l-3.11 14.63c-.234 1.054-.854 1.316-1.731.82l-4.775-3.52-2.303 2.217c-.254.254-.468.468-.96.468l.343-4.863L18.428 5.5c.382-.34-.083-.527-.594-.187L6.57 13.42l-4.678-1.464c-1.017-.318-1.037-.1-.19-1.512L19.95 2.35c.847-.318 1.586.187 1.247 1.348z" stroke-width="2" stroke-linejoin="round"/>
                    </svg>
                    <span>Telegram</span>
                </a>
            </div>
            <p class="copyright">© 2026 PERFUMS. Всі права захищені.</p>
        </div>
    </footer>

    <script>
        // Create particles
        const particlesContainer = document.getElementById('particles');
        for (let i = 0; i < 30; i++) {
            const particle = document.createElement('div');
            particle.className = 'particle';
            particle.style.left = Math.random() * 100 + '%';
            particle.style.animationDelay = Math.random() * 20 + 's';
            particle.style.animationDuration = (15 + Math.random() * 10) + 's';
            particlesContainer.appendChild(particle);
        }

        // Mobile menu toggle
        const menuToggle = document.getElementById('menuToggle');
        const nav = document.getElementById('nav');
        
        menuToggle.addEventListener('click', () => {
            menuToggle.classList.toggle('active');
            nav.classList.toggle('active');
        });

        // Close menu when clicking on a link
        document.querySelectorAll('nav a').forEach(link => {
            link.addEventListener('click', () => {
                menuToggle.classList.remove('active');
                nav.classList.remove('active');
            });
        });

        // Close menu when clicking outside
        document.addEventListener('click', (e) => {
            if (!nav.contains(e.target) && !menuToggle.contains(e.target)) {
                menuToggle.classList.remove('active');
                nav.classList.remove('active');
            }
        });

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

        // Header scroll effect
        const header = document.getElementById('header');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 100) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });

        // Scroll progress bar
        const scrollProgress = document.getElementById('scrollProgress');
        window.addEventListener('scroll', () => {
            const windowHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (window.scrollY / windowHeight) * 100;
            scrollProgress.style.width = scrolled + '%';
        });

        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
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

        // Observe features
        document.querySelectorAll('.feature').forEach(feature => {
            feature.style.opacity = '0';
            feature.style.transform = 'translateY(30px)';
            feature.style.transition = 'all 0.8s ease';
            observer.observe(feature);
        });

        // Observe product cards
        document.querySelectorAll('.product-card').forEach((card, index) => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(40px)';
            card.style.transition = 'all 0.8s cubic-bezier(0.4, 0, 0.2, 1)';
            
            setTimeout(() => {
                card.style.opacity = '1';
                card.style.transform = 'translateY(0)';
            }, 200 + (index * 150));
        });

        // Observe fragrance items
        document.querySelectorAll('.fragrance-item').forEach(item => {
            item.style.opacity = '0';
            item.style.transform = 'translateY(20px)';
            item.style.transition = 'all 0.6s ease';
            observer.observe(item);
        });

        // Observe category sections
        document.querySelectorAll('.category-section').forEach(section => {
            section.style.opacity = '0';
            section.style.transform = 'translateY(30px)';
            section.style.transition = 'all 0.8s ease';
            observer.observe(section);
        });
    </script>
</body>
</html>
