<
``html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bloom Beauty — Luxury Spa & Beauty Studio</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        *, *::before, *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --pink-light: #FDF2F8;
            --pink: #F9A8D4;
            --pink-deep: #EC4899;
            --gold: #D4A574;
            --gold-light: #E8C9A0;
            --gold-dark: #B8864E;
            --cream: #FFFBF5;
            --dark: #1F1218;
            --dark-soft: #3D2B35;
            --gray: #6B5B65;
            --gray-light: #A89BA2;
            --white: #FFFFFF;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Lato', sans-serif;
            color: var(--dark);
            background: var(--cream);
            overflow-x: hidden;
            line-height: 1.7;
        }

        h1, h2, h3, h4, h5, h6 {
            font-family: 'Playfair Display', serif;
            font-weight: 500;
            line-height: 1.3;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 24px;
        }

        /* ===== NAVBAR ===== */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            padding: 20px 0;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .navbar.scrolled {
            background: rgba(255, 251, 245, 0.95);
            backdrop-filter: blur(20px);
            box-shadow: 0 1px 30px rgba(0, 0, 0, 0.06);
            padding: 12px 0;
        }

        .navbar .container {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 28px;
            font-weight: 600;
            color: var(--white);
            text-decoration: none;
            transition: color 0.3s;
        }

        .navbar.scrolled .logo {
            color: var(--dark);
        }

        .logo span {
            color: var(--gold);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 36px;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--white);
            font-size: 14px;
            font-weight: 400;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            transition: color 0.3s;
            position: relative;
        }

        .navbar.scrolled .nav-links a {
            color: var(--dark-soft);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            width: 0;
            height: 1.5px;
            background: var(--gold);
            transition: width 0.3s;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-links a:hover {
            color: var(--gold);
        }

        .nav-btn {
            padding: 10px 28px;
            background: var(--gold);
            color: var(--white) !important;
            border-radius: 50px;
            font-size: 13px !important;
            letter-spacing: 1.5px !important;
            transition: all 0.3s !important;
        }

        .nav-btn::after {
            display: none !important;
        }

        .nav-btn:hover {
            background: var(--gold-dark) !important;
            transform: translateY(-1px);
        }

        .menu-toggle {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            z-index: 1001;
        }

        .menu-toggle span {
            width: 28px;
            height: 2px;
            background: var(--white);
            transition: all 0.3s;
        }

        .navbar.scrolled .menu-toggle span {
            background: var(--dark);
        }

        /* ===== HERO ===== */
        .hero {
            position: relative;
            min-height: 100vh;
            display: flex;
            align-items: center;
            overflow: hidden;
        }

        .hero-bg {
            position: absolute;
            inset: 0;
            background: url('https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/12871c7a8-c9f9-4cb3-a61c-5adff08d56ad.png') center/cover no-repeat;
        }

        .hero-overlay {
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(31, 18, 24, 0.7) 0%, rgba(31, 18, 24, 0.3) 50%, rgba(212, 165, 116, 0.2) 100%);
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 700px;
        }

        .hero-badge {
            display: inline-block;
            padding: 8px 24px;
            border: 1px solid rgba(212, 165, 116, 0.5);
            border-radius: 50px;
            color: var(--gold-light);
            font-size: 12px;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 24px;
            backdrop-filter: blur(10px);
            background: rgba(212, 165, 116, 0.1);
            opacity: 0;
            transform: translateY(20px);
            animation: fadeUp 0.8s 0.3s forwards;
        }

        .hero h1 {
            font-size: clamp(42px, 6vw, 72px);
            color: var(--white);
            margin-bottom: 20px;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeUp 0.8s 0.5s forwards;
        }

        .hero h1 em {
            color: var(--gold-light);
            font-style: italic;
        }

        .hero p {
            font-size: 18px;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 36px;
            max-width: 500px;
            line-height: 1.8;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeUp 0.8s 0.7s forwards;
        }

        .hero-buttons {
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeUp 0.8s 0.9s forwards;
        }

        .btn-primary {
            padding: 16px 40px;
            background: var(--gold);
            color: var(--white);
            border: none;
            border-radius: 50px;
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary:hover {
            background: var(--gold-dark);
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(212, 165, 116, 0.3);
        }

        .btn-outline {
            padding: 16px 40px;
            background: transparent;
            color: var(--white);
            border: 1.5px solid rgba(255, 255, 255, 0.4);
            border-radius: 50px;
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
        }

        .btn-outline:hover {
            border-color: var(--gold);
            color: var(--gold-light);
            background: rgba(212, 165, 116, 0.1);
        }

        .hero-scroll {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 2;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            color: rgba(255, 255, 255, 0.5);
            font-size: 11px;
            letter-spacing: 2px;
            text-transform: uppercase;
            animation: float 3s ease-in-out infinite;
        }

        .scroll-line {
            width: 1px;
            height: 40px;
            background: linear-gradient(to bottom, rgba(255, 255, 255, 0.5), transparent);
        }

        /* ===== FLOATING STATS ===== */
        .hero-stats {
            position: absolute;
            right: 80px;
            bottom: 120px;
            z-index: 2;
            display: flex;
            flex-direction: column;
            gap: 32px;
        }

        .stat-item {
            text-align: center;
            color: var(--white);
        }

        .stat-number {
            font-family: 'Playfair Display', serif;
            font-size: 36px;
            font-weight: 600;
            color: var(--gold-light);
        }

        .stat-label {
            font-size: 11px;
            letter-spacing: 2px;
            text-transform: uppercase;
            opacity: 0.7;
        }

        /* ===== SECTION STYLES ===== */
        .section {
            padding: 100px 0;
        }

        .section-header {
            text-align: center;
            margin-bottom: 64px;
        }

        .section-tag {
            display: inline-block;
            color: var(--gold);
            font-size: 12px;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 16px;
            font-weight: 700;
        }

        .section-title {
            font-size: clamp(32px, 4vw, 48px);
            color: var(--dark);
            margin-bottom: 20px;
        }

        .section-subtitle {
            font-size: 17px;
            color: var(--gray);
            max-width: 560px;
            margin: 0 auto;
            line-height: 1.8;
        }

        .section-divider {
            width: 60px;
            height: 2px;
            background: linear-gradient(to right, var(--gold), var(--pink));
            margin: 20px auto 0;
            border-radius: 2px;
        }

        /* ===== SERVICES ===== */
        .services {
            background: var(--white);
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 32px;
        }

        .service-card {
            background: var(--cream);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
            position: relative;
        }

        .service-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.08);
        }

        .service-img {
            width: 100%;
            height: 280px;
            object-fit: cover;
            transition: transform 0.6s;
        }

        .service-card:hover .service-img {
            transform: scale(1.05);
        }

        .service-img-wrapper {
            overflow: hidden;
            position: relative;
        }

        .service-img-wrapper::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 60px;
            background: linear-gradient(to top, var(--cream), transparent);
        }

        .service-body {
            padding: 28px 32px 32px;
        }

        .service-icon {
            width: 48px;
            height: 48px;
            background: linear-gradient(135deg, var(--gold), var(--gold-light));
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 16px;
            font-size: 22px;
        }

        .service-body h3 {
            font-size: 22px;
            margin-bottom: 10px;
            color: var(--dark);
        }

        .service-body p {
            font-size: 15px;
            color: var(--gray);
            line-height: 1.7;
            margin-bottom: 20px;
        }

        .service-price {
            font-family: 'Playfair Display', serif;
            font-size: 20px;
            color: var(--gold-dark);
            font-weight: 600;
        }

        .service-price span {
            font-family: 'Lato', sans-serif;
            font-size: 13px;
            color: var(--gray-light);
            font-weight: 400;
        }

        /* ===== ABOUT ===== */
        .about {
            background: var(--cream);
        }

        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 80px;
            align-items: center;
        }

        .about-images {
            position: relative;
        }

        .about-img-main {
            width: 100%;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
        }

        .about-img-float {
            position: absolute;
            bottom: -30px;
            right: -30px;
            width: 200px;
            height: 200px;
            border-radius: 20px;
            object-fit: cover;
            border: 6px solid var(--cream);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .about-badge {
            position: absolute;
            top: -20px;
            left: -20px;
            width: 120px;
            height: 120px;
            background: var(--gold);
            border-radius: 50%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: var(--white);
            box-shadow: 0 10px 30px rgba(212, 165, 116, 0.4);
        }

        .about-badge .badge-num {
            font-family: 'Playfair Display', serif;
            font-size: 32px;
            font-weight: 700;
            line-height: 1;
        }

        .about-badge .badge-text {
            font-size: 10px;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .about-content .section-tag {
            text-align: left;
        }

        .about-content h2 {
            font-size: clamp(32px, 3.5vw, 44px);
            margin-bottom: 24px;
        }

        .about-content p {
            font-size: 16px;
            color: var(--gray);
            line-height: 1.8;
            margin-bottom: 16px;
        }

        .about-features {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
            margin: 32px 0;
        }

        .about-feature {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .about-feature .check {
            width: 28px;
            height: 28px;
            background: rgba(212, 165, 116, 0.15);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--gold);
            font-size: 14px;
            flex-shrink: 0;
        }

        .about-feature span {
            font-size: 14px;
            color: var(--dark-soft);
            font-weight: 400;
        }

        /* ===== PRODUCTS ===== */
        .products {
            background: var(--white);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 32px;
        }

        .product-card {
            background: var(--cream);
            border-radius: 20px;
            padding: 24px;
            text-align: center;
            transition: all 0.4s;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .product-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(to right, var(--gold), var(--pink));
            transform: scaleX(0);
            transition: transform 0.4s;
        }

        .product-card:hover::before {
            transform: scaleX(1);
        }

        .product-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 16px 48px rgba(0, 0, 0, 0.07);
        }

        .product-img-wrap {
            width: 180px;
            height: 180px;
            margin: 0 auto 20px;
            border-radius: 50%;
            overflow: hidden;
            border: 4px solid var(--white);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.06);
        }

        .product-img-wrap img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s;
        }

        .product-card:hover .product-img-wrap img {
            transform: scale(1.1);
        }

        .product-card h3 {
            font-size: 20px;
            margin-bottom: 8px;
        }

        .product-card .product-desc {
            font-size: 14px;
            color: var(--gray);
            margin-bottom: 16px;
            line-height: 1.6;
        }

        .product-price {
            font-family: 'Playfair Display', serif;
            font-size: 24px;
            color: var(--gold-dark);
            font-weight: 600;
            margin-bottom: 16px;
        }

        .btn-add {
            padding: 10px 28px;
            background: transparent;
            border: 1.5px solid var(--gold);
            color: var(--gold-dark);
            border-radius: 50px;
            font-size: 13px;
            font-weight: 700;
            letter-spacing: 1px;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-add:hover {
            background: var(--gold);
            color: var(--white);
        }

        /* ===== TESTIMONIALS ===== */
        .testimonials {
            background: linear-gradient(135deg, var(--dark) 0%, var(--dark-soft) 100%);
            position: relative;
            overflow: hidden;
        }

        .testimonials::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -20%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(212, 165, 116, 0.08) 0%, transparent 70%);
            border-radius: 50%;
        }

        .testimonials .section-tag {
            color: var(--gold-light);
        }

        .testimonials .section-title {
            color: var(--white);
        }

        .testimonials .section-subtitle {
            color: rgba(255, 255, 255, 0.5);
        }

        .testimonials .section-divider {
            background: linear-gradient(to right, var(--gold), var(--pink));
        }

        .testimonial-slider {
            position: relative;
            max-width: 800px;
            margin: 0 auto;
        }

        .testimonial-item {
            display: none;
            text-align: center;
            padding: 0 40px;
            animation: fadeIn 0.5s ease;
        }

        .testimonial-item.active {
            display: block;
        }

        .testimonial-quote {
            font-size: 48px;
            color: var(--gold);
            font-family: 'Playfair Display', serif;
            line-height: 1;
            margin-bottom: 8px;
        }

        .testimonial-text {
            font-size: 20px;
            color: rgba(255, 255, 255, 0.85);
            line-height: 1.8;
            font-style: italic;
            font-family: 'Playfair Display', serif;
            margin-bottom: 32px;
        }

        .testimonial-author {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
        }

        .testimonial-avatar {
            width: 64px;
            height: 64px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--gold), var(--pink));
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Playfair Display', serif;
            font-size: 24px;
            color: var(--white);
            font-weight: 600;
        }

        .testimonial-name {
            font-family: 'Playfair Display', serif;
            font-size: 18px;
            color: var(--white);
        }

        .testimonial-role {
            font-size: 13px;
            color: var(--gold-light);
            letter-spacing: 1px;
        }

        .testimonial-stars {
            color: var(--gold);
            font-size: 16px;
            letter-spacing: 4px;
            margin-bottom: 24px;
        }

        .testimonial-dots {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 40px;
        }

        .t-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.2);
            cursor: pointer;
            transition: all 0.3s;
            border: none;
        }

        .t-dot.active {
            background: var(--gold);
            width: 30px;
            border-radius: 5px;
        }

        /* ===== GALLERY ===== */
        .gallery {
            background: var(--cream);
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-template-rows: repeat(2, 250px);
            gap: 16px;
        }

        .gallery-item {
            border-radius: 16px;
            overflow: hidden;
            position: relative;
            cursor: pointer;
        }

        .gallery-item:nth-child(1) {
            grid-row: span 2;
        }

        .gallery-item:nth-child(4) {
            grid-row: span 2;
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s;
        }

        .gallery-item:hover img {
            transform: scale(1.08);
        }

        .gallery-overlay {
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(31, 18, 24, 0.6), transparent);
            opacity: 0;
            transition: opacity 0.3s;
            display: flex;
            align-items: flex-end;
            padding: 24px;
        }

        .gallery-item:hover .gallery-overlay {
            opacity: 1;
        }

        .gallery-overlay span {
            color: var(--white);
            font-family: 'Playfair Display', serif;
            font-size: 18px;
        }

        /* ===== BOOKING / CONTACT ===== */
        .booking {
            background: var(--white);
            position: relative;
        }

        .booking-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 80px;
            align-items: start;
        }

        .booking-info h2 {
            font-size: clamp(32px, 3.5vw, 44px);
            margin-bottom: 24px;
        }

        .booking-info p {
            font-size: 16px;
            color: var(--gray);
            line-height: 1.8;
            margin-bottom: 32px;
        }

        .contact-details {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 16px;
        }

        .contact-icon {
            width: 48px;
            height: 48px;
            background: var(--pink-light);
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            flex-shrink: 0;
        }

        .contact-item-text h4 {
            font-size: 15px;
            margin-bottom: 2px;
        }

        .contact-item-text p {
            font-size: 14px;
            color: var(--gray);
            margin: 0;
        }

        .booking-form {
            background: var(--cream);
            padding: 48px;
            border-radius: 24px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.05);
        }

        .booking-form h3 {
            font-size: 26px;
            margin-bottom: 28px;
            text-align: center;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            font-size: 13px;
            font-weight: 700;
            letter-spacing: 1px;
            text-transform: uppercase;
            color: var(--dark-soft);
            margin-bottom: 8px;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 14px 18px;
            border: 1.5px solid #E8E0E5;
            border-radius: 12px;
            font-family: 'Lato', sans-serif;
            font-size: 15px;
            color: var(--dark);
            background: var(--white);
            transition: all 0.3s;
            outline: none;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            border-color: var(--gold);
            box-shadow: 0 0 0 3px rgba(212, 165, 116, 0.15);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 100px;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }

        .btn-submit {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            color: var(--white);
            border: none;
            border-radius: 12px;
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 8px;
        }

        .btn-submit:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(212, 165, 116, 0.4);
        }

        /* ===== NEWSLETTER ===== */
        .newsletter {
            background: linear-gradient(135deg, var(--pink-light) 0%, #FDE8F0 100%);
            padding: 80px 0;
        }

        .newsletter-content {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }

        .newsletter-content h2 {
            font-size: 36px;
            margin-bottom: 16px;
        }

        .newsletter-content p {
            font-size: 16px;
            color: var(--gray);
            margin-bottom: 32px;
        }

        .newsletter-form {
            display: flex;
            gap: 12px;
            max-width: 480px;
            margin: 0 auto;
        }

        .newsletter-form input {
            flex: 1;
            padding: 16px 24px;
            border: 1.5px solid rgba(212, 165, 116, 0.3);
            border-radius: 50px;
            font-family: 'Lato', sans-serif;
            font-size: 15px;
            outline: none;
            background: var(--white);
            transition: all 0.3s;
        }

        .newsletter-form input:focus {
            border-color: var(--gold);
            box-shadow: 0 0 0 3px rgba(212, 165, 116, 0.15);
        }

        .newsletter-form button {
            padding: 16px 32px;
            background: var(--gold);
            color: var(--white);
            border: none;
            border-radius: 50px;
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 1px;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.3s;
            white-space: nowrap;
        }

        .newsletter-form button:hover {
            background: var(--gold-dark);
        }

        /* ===== FOOTER ===== */
        .footer {
            background: var(--dark);
            color: rgba(255, 255, 255, 0.7);
            padding: 80px 0 0;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 48px;
            padding-bottom: 60px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
        }

        .footer-brand .logo {
            display: inline-block;
            margin-bottom: 20px;
        }

        .footer-brand p {
            font-size: 15px;
            line-height: 1.8;
            margin-bottom: 24px;
        }

        .social-links {
            display: flex;
            gap: 12px;
        }

        .social-link {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.08);
            display: flex;
            align-items: center;
            justify-content: center;
            color: rgba(255, 255, 255, 0.7);
            text-decoration: none;
            transition: all 0.3s;
            font-size: 16px;
        }

        .social-link:hover {
            background: var(--gold);
            color: var(--white);
            transform: translateY(-2px);
        }

        .footer-col h4 {
            font-family: 'Playfair Display', serif;
            font-size: 18px;
            color: var(--white);
            margin-bottom: 24px;
        }

        .footer-col ul {
            list-style: none;
        }

        .footer-col ul li {
            margin-bottom: 12px;
        }

        .footer-col ul a {
            color: rgba(255, 255, 255, 0.6);
            text-decoration: none;
            font-size: 14px;
            transition: all 0.3s;
        }

        .footer-col ul a:hover {
            color: var(--gold-light);
            padding-left: 4px;
        }

        .footer-bottom {
            padding: 24px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 13px;
            color: rgba(255, 255, 255, 0.4);
        }

        .footer-bottom a {
            color: rgba(255, 255, 255, 0.4);
            text-decoration: none;
        }

        .footer-bottom a:hover {
            color: var(--gold-light);
        }

        /* ===== BACK TO TOP ===== */
        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 48px;
            height: 48px;
            background: var(--gold);
            color: var(--white);
            border: none;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
            z-index: 999;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s;
            box-shadow: 0 4px 20px rgba(212, 165, 116, 0.4);
        }

        .back-to-top.visible {
            opacity: 1;
            visibility: visible;
        }

        .back-to-top:hover {
            transform: translateY(-3px);
            background: var(--gold-dark);
        }

        /* ===== ANIMATIONS ===== */
        @keyframes fadeUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes float {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(10px); }
        }

        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* ===== MOBILE NAV ===== */
        .mobile-menu {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(31, 18, 24, 0.98);
            z-index: 999;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 32px;
        }

        .mobile-menu.open {
            display: flex;
        }

        .mobile-menu a {
            color: var(--white);
            text-decoration: none;
            font-family: 'Playfair Display', serif;
            font-size: 28px;
            transition: color 0.3s;
        }

        .mobile-menu a:hover {
            color: var(--gold-light);
        }

        .mobile-close {
            position: absolute;
            top: 24px;
            right: 24px;
            background: none;
            border: none;
            color: var(--white);
            font-size: 32px;
            cursor: pointer;
        }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 1024px) {
            .hero-stats {
                display: none;
            }

            .about-grid {
                grid-template-columns: 1fr;
                gap: 48px;
            }

            .booking-grid {
                grid-template-columns: 1fr;
                gap: 48px;
            }

            .footer-grid {
                grid-template-columns: 1fr 1fr;
            }

            .gallery-grid {
                grid-template-columns: repeat(2, 1fr);
                grid-template-rows: repeat(3, 200px);
            }

            .gallery-item:nth-child(1),
            .gallery-item:nth-child(4) {
                grid-row: span 1;
            }
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .menu-toggle {
                display: flex;
            }

            .hero h1 {
                font-size: 36px;
            }

            .hero p {
                font-size: 16px;
            }

            .hero-buttons {
                flex-direction: column;
            }

            .btn-primary, .btn-outline {
                text-align: center;
            }

            .services-grid {
                grid-template-columns: 1fr;
            }

            .products-grid {
                grid-template-columns: 1fr;
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .booking-form {
                padding: 32px 24px;
            }

            .newsletter-form {
                flex-direction: column;
            }

            .footer-grid {
                grid-template-columns: 1fr;
            }

            .footer-bottom {
                flex-direction: column;
                gap: 8px;
                text-align: center;
            }

            .gallery-grid {
                grid-template-columns: 1fr;
                grid-template-rows: auto;
            }

            .gallery-item {
                height: 250px;
            }

            .about-img-float {
                width: 140px;
                height: 140px;
                right: -10px;
                bottom: -10px;
            }

            .about-badge {
                width: 90px;
                height: 90px;
                top: -10px;
                left: -10px;
            }

            .about-badge .badge-num {
                font-size: 24px;
            }
        }

        /* ===== TOAST ===== */
        .toast {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: var(--dark);
            color: var(--white);
            padding: 16px 32px;
            border-radius: 12px;
            font-size: 14px;
            z-index: 9999;
            transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
        }

        .toast.show {
            transform: translateX(-50%) translateY(0);
        }
    </style>
</head>
<body>

    <!-- NAVBAR -->
    <nav class="navbar" id="navbar">
        <div class="container">
            <a href="#" class="logo">Bloom<span>.</span></a>
            <ul class="nav-links">
                <li><a href="#services">Services</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#products">Products</a></li>
                <li><a href="#gallery">Gallery</a></li>
                <li><a href="#testimonials">Reviews</a></li>
                <li><a href="#booking" class="nav-btn">Book Now</a></li>
            </ul>
            <div class="menu-toggle" id="menuToggle" onclick="toggleMobileMenu()">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- MOBILE MENU -->
    <div class="mobile-menu" id="mobileMenu">
        <button class="mobile-close" onclick="toggleMobileMenu()">✕</button>
        <a href="#services" onclick="toggleMobileMenu()">Services</a>
        <a href="#about" onclick="toggleMobileMenu()">About</a>
        <a href="#products" onclick="toggleMobileMenu()">Products</a>
        <a href="#gallery" onclick="toggleMobileMenu()">Gallery</a>
        <a href="#testimonials" onclick="toggleMobileMenu()">Reviews</a>
        <a href="#booking" onclick="toggleMobileMenu()">Book Now</a>
    </div>

    <!-- HERO -->
    <section class="hero" id="hero">
        <div class="hero-bg"></div>
        <div class="hero-overlay"></div>
        <div class="container">
            <div class="hero-content">
                <div class="hero-badge"> Premium Beauty Experience</div>
                <h1>Discover Your <em>Natural</em> Beauty</h1>
                <p>Indulge in luxurious treatments designed to rejuvenate your skin, refresh your spirit, and reveal your most radiant self.</p>
                <div class="hero-buttons">
                    <a href="#booking" class="btn-primary">Book Appointment</a>
                    <a href="#services" class="btn-outline">Explore Services</a>
                </div>
            </div>
        </div>
        <div class="hero-stats">
            <div class="stat-item">
                <div class="stat-number" data-count="15">0</div>
                <div class="stat-label">Years Experience</div>
            </div>
            <div class="stat-item">
                <div class="stat-number" data-count="5000">0</div>
                <div class="stat-label">Happy Clients</div>
            </div>
            <div class="stat-item">
                <div class="stat-number" data-count="50">0</div>
                <div class="stat-label">Expert Staff</div>
            </div>
        </div>
        <div class="hero-scroll">
            <span>Scroll</span>
            <div class="scroll-line"></div>
        </div>
    </section>

    <!-- SERVICES -->
    <section class="section services" id="services">
        <div class="container">
            <div class="section-header reveal">
                <div class="section-tag">What We Offer</div>
                <h2 class="section-title">Our Premium Services</h2>
                <p class="section-subtitle">Experience a world of beauty and relaxation with our carefully curated treatments, each designed to bring out your natural radiance.</p>
                <div class="section-divider"></div>
            </div>
            <div class="services-grid">
                <div class="service-card reveal">
                    <div class="service-img-wrapper">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/1c338b61d-13d9-4878-b4de-3840f883a03f.png" alt="Facial Treatment" class="service-img">
                    </div>
                    <div class="service-body">
                        <div class="service-icon"></div>
                        <h3>Facial Treatment</h3>
                        <p>Deep cleansing and rejuvenating facial treatments using premium organic products for a radiant glow.</p>
                        <div class="service-price">$120 <span>/ 60 min</span></div>
                    </div>
                </div>
                <div class="service-card reveal">
                    <div class="service-img-wrapper">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/175f0e62d-2771-4f03-86e4-b1c2b831b81c.png" alt="Hair Styling" class="service-img">
                    </div>
                    <div class="service-body">
                        <div class="service-icon">✦</div>
                        <h3>Hair Styling</h3>
                        <p>Expert haircuts, coloring, and styling services by our talented team of professional hair artists.</p>
                        <div class="service-price">$85 <span>/ session</span></div>
                    </div>
                </div>
                <div class="service-card reveal">
                    <div class="service-img-wrapper">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/15faa0b37-93a1-4a2c-b272-c74b72853bbc.png" alt="Nail Art" class="service-img">
                    </div>
                    <div class="service-body">
                        <div class="service-icon">✦</div>
                        <h3>Nail Art & Spa</h3>
                        <p>Luxurious manicure and pedicure services with creative nail art designs and spa treatments.</p>
                        <div class="service-price">$65 <span>/ session</span></div>
                    </div>
                </div>
                <div class="service-card reveal">
                    <div class="service-img-wrapper">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/12871c7a8-c9f9-4cb3-a61c-5adff08d56ad.png" alt="Body Massage" class="service-img">
                    </div>
                    <div class="service-body">
                        <div class="service-icon">✦</div>
                        <h3>Body Massage</h3>
                        <p>Relaxing full-body massage therapies using essential oils and aromatherapy techniques.</p>
                        <div class="service-price">$150 <span>/ 90 min</span></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ABOUT -->
    <section class="section about" id="about">
        <div class="container">
            <div class="about-grid">
                <div class="about-images reveal">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/1c338b61d-13d9-4878-b4de-3840f883a03f.png" alt="About Bloom Beauty" class="about-img-main">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/12871c7a8-c9f9-4cb3-a61c-5adff08d56ad.png" alt="Beauty Products" class="about-img-float">
                    <div class="about-badge">
                        <span class="badge-num">15+</span>
                        <span class="badge-text">Years</span>
                    </div>
                </div>
                <div class="about-content reveal">
                    <div class="section-tag">Our Story</div>
                    <h2>A Legacy of Beauty & Excellence</h2>
                    <p>Founded in 2011, Bloom Beauty has been at the forefront of luxury beauty services. Our mission is to help every client discover and embrace their unique beauty through personalized treatments and expert care.</p>
                    <p>We combine traditional techniques with cutting-edge technology, using only the finest organic and cruelty-free products to deliver exceptional results.</p>
                    <div class="about-features">
                        <div class="about-feature">
                            <div class="check">✓</div>
                            <span>Organic Products</span>
                        </div>
                        <div class="about-feature">
                            <div class="check">✓</div>
                            <span>Expert Therapists</span>
                        </div>
                        <div class="about-feature">
                            <div class="check">✓</div>
                            <span>Cruelty Free</span>
                        </div>
                        <div class="about-feature">
                            <div class="check">✓</div>
                            <span>Personalized Care</span>
                        </div>
                        <div class="about-feature">
                            <div class="check">✓</div>
                            <span>Luxury Environment</span>
                        </div>
                        <div class="about-feature">
                            <div class="check">✓</div>
                            <span>Award Winning</span>
                        </div>
                    </div>
                    <a href="#booking" class="btn-primary">Learn More</a>
                </div>
            </div>
        </div>
    </section>

    <!-- PRODUCTS -->
    <section class="section products" id="products">
        <div class="container">
            <div class="section-header reveal">
                <div class="section-tag">Shop Now</div>
                <h2 class="section-title">Featured Products</h2>
                <p class="section-subtitle">Discover our curated collection of premium skincare and beauty products, formulated with natural ingredients for visible results.</p>
                <div class="section-divider"></div>
            </div>
            <div class="products-grid">
                <div class="product-card reveal">
                    <div class="product-img-wrap">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/1a97a9b7d-88b6-4502-bbb2-e06ecd75dabf.png" alt="Rose Serum">
                    </div>
                    <h3>Rose Gold Serum</h3>
                    <p class="product-desc">Hydrating facial serum with rose extract and 24K gold particles</p>
                    <div class="product-price">$89</div>
                    <button class="btn-add" onclick="addToCart('Rose Gold Serum')">Add to Cart</button>
                </div>
                <div class="product-card reveal">
                    <div class="product-img-wrap">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/1a97a9b7d-88b6-4502-bbb2-e06ecd75dabf.png" alt="Cream">
                    </div>
                    <h3>Luxury Night Cream</h3>
                    <p class="product-desc">Intensive overnight repair cream with peptides and botanical extracts</p>
                    <div class="product-price">$75</div>
                    <button class="btn-add" onclick="addToCart('Luxury Night Cream')">Add to Cart</button>
                </div>
                <div class="product-card reveal">
                    <div class="product-img-wrap">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/12871c7a8-c9f9-4cb3-a61c-5adff08d56ad.png" alt="Body Oil">
                    </div>
                    <h3>Botanical Body Oil</h3>
                    <p class="product-desc">Nourishing body oil blend with lavender, jasmine, and sweet almond</p>
                    <div class="product-price">$58</div>
                    <button class="btn-add" onclick="addToCart('Botanical Body Oil')">Add to Cart</button>
                </div>
                <div class="product-card reveal">
                    <div class="product-img-wrap">
                        <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/12871c7a8-c9f9-4cb3-a61c-5adff08d56ad.png" alt="Face Mask">
                    </div>
                    <h3>Clay Face Mask</h3>
                    <p class="product-desc">Purifying clay mask with charcoal and tea tree for deep cleansing</p>
                    <div class="product-price">$42</div>
                    <button class="btn-add" onclick="addToCart('Clay Face Mask')">Add to Cart</button>
                </div>
            </div>
        </div>
    </section>

    <!-- TESTIMONIALS -->
    <section class="section testimonials" id="testimonials">
        <div class="container">
            <div class="section-header reveal">
                <div class="section-tag">Testimonials</div>
                <h2 class="section-title">What Our Clients Say</h2>
                <p class="section-subtitle">Real stories from real clients who have experienced the Bloom difference.</p>
                <div class="section-divider"></div>
            </div>
            <div class="testimonial-slider reveal">
                <div class="testimonial-item active">
                    <div class="testimonial-quote">"</div>
                    <div class="testimonial-stars">★ ★ ★ ★ ★</div>
                    <p class="testimonial-text">Bloom Beauty has completely transformed my skincare routine. The facial treatments are absolutely divine, and my skin has never looked better. The staff is incredibly professional and attentive.</p>
                    <div class="testimonial-author">
                        <div class="testimonial-avatar">S</div>
                        <div class="testimonial-name">Sarah Mitchell</div>
                        <div class="testimonial-role">Loyal Client • 3 Years</div>
                    </div>
                </div>
                <div class="testimonial-item">
                    <div class="testimonial-quote">"</div>
                    <div class="testimonial-stars">★ ★ ★ ★ ★</div>
                    <p class="testimonial-text">From the moment I walked in, I felt like royalty. The ambiance is luxurious, the treatments are world-class, and the results speak for themselves. Bloom is my go-to beauty destination.</p>
                    <div class="testimonial-author">
                        <div class="testimonial-avatar">E</div>
                        <div class="testimonial-name">Emma Rodriguez</div>
                        <div class="testimonial-role">VIP Member • 5 Years</div>
                    </div>
                </div>
                <div class="testimonial-item">
                    <div class="testimonial-quote">"</div>
                    <div class="testimonial-stars">★ ★ ★ ★ ★</div>
                    <p class="testimonial-text">I've tried many salons over the years, but nothing compares to Bloom. Their hair styling team is phenomenal, and the products they use are top-notch. I always leave feeling amazing!</p>
                    <div class="testimonial-author">
                        <div class="testimonial-avatar">J</div>
                        <div class="testimonial-name">Jessica Chen</div>
                        <div class="testimonial-role">Regular Client • 2 Years</div>
                    </div>
                </div>
                <div class="testimonial-dots">
                    <button class="t-dot active" onclick="goToSlide(0)"></button>
                    <button class="t-dot" onclick="goToSlide(1)"></button>
                    <button class="t-dot" onclick="goToSlide(2)"></button>
                </div>
            </div>
        </div>
    </section>

    <!-- GALLERY -->
    <section class="section gallery" id="gallery">
        <div class="container">
            <div class="section-header reveal">
                <div class="section-tag">Our Gallery</div>
                <h2 class="section-title">A Glimpse Inside</h2>
                <p class="section-subtitle">Step into our world of beauty and see what makes Bloom Beauty a truly special place.</p>
                <div class="section-divider"></div>
            </div>
            <div class="gallery-grid reveal">
                <div class="gallery-item">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/1c338b61d-13d9-4878-b4de-3840f883a03f.png" alt="Spa Interior">
                    <div class="gallery-overlay"><span>Spa Treatment Room</span></div>
                </div>
                <div class="gallery-item">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/12871c7a8-c9f9-4cb3-a61c-5adff08d56ad.png" alt="Beauty Products">
                    <div class="gallery-overlay"><span>Premium Products</span></div>
                </div>
                <div class="gallery-item">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/1a97a9b7d-88b6-4502-bbb2-e06ecd75dabf.png" alt="Skincare">
                    <div class="gallery-overlay"><span>Skincare Rituals</span></div>
                </div>
                <div class="gallery-item">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/175f0e62d-2771-4f03-86e4-b1c2b831b81c.png" alt="Hair Salon">
                    <div class="gallery-overlay"><span>Hair Studio</span></div>
                </div>
                <div class="gallery-item">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/15faa0b37-93a1-4a2c-b272-c74b72853bbc.png" alt="Nail Studio">
                    <div class="gallery-overlay"><span>Nail Art Studio</span></div>
                </div>
                <div class="gallery-item">
                    <img src="https://image.qwenlm.ai/public_source/6d761220-5a7e-4ceb-b930-ac16225ffa4d/12871c7a8-c9f9-4cb3-a61c-5adff08d56ad.png" alt="Relaxation">
                    <div class="gallery-overlay"><span>Relaxation Zone</span></div>
                </div>
            </div>
        </div>
    </section>

    <!-- BOOKING -->
    <section class="section booking" id="booking">
        <div class="container">
            <div class="booking-grid">
                <div class="booking-info reveal">
                    <div class="section-tag">Get in Touch</div>
                    <h2>Book Your Beauty Experience</h2>
                    <p>Ready to transform your look and feel? Schedule your appointment today and let our expert team create a personalized beauty experience just for you.</p>
                    <div class="contact-details">
                        <div class="contact-item">
                            <div class="contact-icon">📍</div>
                            <div class="contact-item-text">
                                <h4>Visit Us</h4>
                                <p>123 Beauty Lane, Beverly Hills, CA 90210</p>
                            </div>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">📞</div>
                            <div class="contact-item-text">
                                <h4>Call Us</h4>
                                <p>+1 (555) 123-4567</p>
                            </div>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">✉️</div>
                            <div class="contact-item-text">
                                <h4>Email Us</h4>
                                <p>hello@bloombeauty.com</p>
                            </div>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">🕐</div>
                            <div class="contact-item-text">
                                <h4>Working Hours</h4>
                                <p>Mon - Sat: 9:00 AM - 8:00 PM</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="booking-form reveal">
                    <h3>Schedule Appointment</h3>
                    <form id="bookingForm" onsubmit="handleSubmit(event)">
                        <div class="form-row">
                            <div class="form-group">
                                <label>First Name</label>
                                <input type="text" placeholder="Your first name" required>
                            </div>
                            <div class="form-group">
                                <label>Last Name</label>
                                <input type="text" placeholder="Your last name" required>
                            </div>
                        </div>
                        <div class="form-group">
                            <label>Email Address</label>
                            <input type="email" placeholder="your@email.com" required>
                        </div>
                        <div class="form-group">
                            <label>Phone Number</label>
                            <input type="tel" placeholder="+1 (555) 000-0000">
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label>Service</label>
                                <select required>
                                    <option value="">Select service</option>
                                    <option>Facial Treatment</option>
                                    <option>Hair Styling</option>
                                    <option>Nail Art & Spa</option>
                                    <option>Body Massage</option>
                                    <option>Full Beauty Package</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Preferred Date</label>
                                <input type="date" required>
                            </div>
                        </div>
                        <div class="form-group">
                            <label>Special Requests</label>
                            <textarea placeholder="Any special requests or preferences..."></textarea>
                        </div>
                        <button type="submit" class="btn-submit">Book Appointment</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- NEWSLETTER -->
    <section class="newsletter">
        <div class="container">
            <div class="newsletter-content reveal">
                <h2>Stay Beautiful</h2>
                <p>Subscribe to our newsletter for exclusive offers, beauty tips, and the latest trends delivered straight to your inbox.</p>
                <form class="newsletter-form" onsubmit="handleNewsletter(event)">
                    <input type="email" placeholder="Enter your email address" required>
                    <button type="submit">Subscribe</button>
                </form>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="footer">
        <div class="container">
            <div class="footer-grid">
                <div class="footer-brand">
                    <a href="#" class="logo">Bloom<span>.</span></a>
                    <p>Where beauty meets luxury. We are dedicated to helping you discover and celebrate your unique radiance through premium treatments and personalized care.</p>
                    <div class="social-links">
                        <a href="#" class="social-link" aria-label="Facebook">f</a>
                        <a href="#" class="social-link" aria-label="Instagram">ig</a>
                        <a href="#" class="social-link" aria-label="Twitter">tw</a>
                        <a href="#" class="social-link" aria-label="Pinterest">pin</a>
                    </div>
                </div>
                <div class="footer-col">
                    <h4>Quick Links</h4>
                    <ul>
                        <li><a href="#services">Services</a></li>
                        <li><a href="#about">About Us</a></li>
                        <li><a href="#products">Products</a></li>
                        <li><a href="#gallery">Gallery</a></li>
                        <li><a href="#booking">Contact</a></li>
                    </ul>
                </div>
                <div class="footer-col">
                    <h4>Services</h4>
                    <ul>
                        <li><a href="#">Facial Treatment</a></li>
                        <li><a href="#">Hair Styling</a></li>
                        <li><a href="#">Nail Art & Spa</a></li>
                        <li><a href="#">Body Massage</a></li>
                        <li><a href="#">Bridal Package</a></li>
                    </ul>
                </div>
                <div class="footer-col">
                    <h4>Support</h4>
                    <ul>
                        <li><a href="#">FAQ</a></li>
                        <li><a href="#">Privacy Policy</a></li>
                        <li><a href="#">Terms of Service</a></li>
                        <li><a href="#">Gift Cards</a></li>
                        <li><a href="#">Careers</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>© 2026 Bloom Beauty. All rights reserved.</p>
                <p>Crafted with ♥ for beauty lovers</p>
            </div>
        </div>
    </footer>

    <!-- BACK TO TOP -->
    <button class="back-to-top" id="backToTop" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">↑</button>

    <!-- TOAST -->
    <div class="toast" id="toast"></div>

    <script>
        // Navbar scroll effect
        const navbar = document.getElementById('navbar');
        const backToTop = document.getElementById('backToTop');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 80) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }

            if (window.scrollY > 600) {
                backToTop.classList.add('visible');
            } else {
                backToTop.classList.remove('visible');
            }
        });

        // Mobile menu
        function toggleMobileMenu() {
            const menu = document.getElementById('mobileMenu');
            menu.classList.toggle('open');
            document.body.style.overflow = menu.classList.contains('open') ? 'hidden' : '';
        }

        // Reveal on scroll
        const revealElements = document.querySelectorAll('.reveal');
        const revealObserver = new IntersectionObserver((entries) => {
            entries.forEach((entry, index) => {
                if (entry.isIntersecting) {
                    setTimeout(() => {
                        entry.target.classList.add('visible');
                    }, index * 100);
                    revealObserver.unobserve(entry.target);
                }
            });
        }, { threshold: 0.15, rootMargin: '0px 0px -50px 0px' });

        revealElements.forEach(el => revealObserver.observe(el));

        // Counter animation
        function animateCounters() {
            const counters = document.querySelectorAll('.stat-number');
            counters.forEach(counter => {
                const target = parseInt(counter.getAttribute('data-count'));
                const duration = 2000;
                const start = performance.now();

                function update(currentTime) {
                    const elapsed = currentTime - start;
                    const progress = Math.min(elapsed / duration, 1);
                    const eased = 1 - Math.pow(1 - progress, 3);
                    const current = Math.floor(eased * target);

                    if (target >= 1000) {
                        counter.textContent = current.toLocaleString() + '+';
                    } else {
                        counter.textContent = current + '+';
                    }

                    if (progress < 1) {
                        requestAnimationFrame(update);
                    }
                }
                requestAnimationFrame(update);
            });
        }

        const heroObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateCounters();
                    heroObserver.unobserve(entry.target);
                }
            });
        }, { threshold: 0.5 });

        const statsSection = document.querySelector('.hero-stats');
        if (statsSection) heroObserver.observe(statsSection);

        // Testimonial slider
        let currentSlide = 0;
        const slides = document.querySelectorAll('.testimonial-item');
        const dots = document.querySelectorAll('.t-dot');

        function goToSlide(index) {
            slides[currentSlide].classList.remove('active');
            dots[currentSlide].classList.remove('active');
            currentSlide = index;
            slides[currentSlide].classList.add('active');
            dots[currentSlide].classList.add('active');
        }

        // Auto-rotate testimonials
        setInterval(() => {
            goToSlide((currentSlide + 1) % slides.length);
        }, 5000);

        // Toast notification
        function showToast(message) {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 3000);
        }

        // Add to cart
        function addToCart(productName) {
            showToast('✓ ' + productName + ' added to cart!');
        }

        // Form submission
        function handleSubmit(e) {
            e.preventDefault();
            showToast('✓ Appointment booked successfully! We\'ll contact you soon.');
            e.target.reset();
        }

        // Newsletter
        function handleNewsletter(e) {
            e.preventDefault();
            showToast('✓ Subscribed successfully! Welcome to Bloom Beauty.');
            e.target.reset();
        }

        // Smooth scroll for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                e.preventDefault();
                const targetEl = document.querySelector(targetId);
                if (targetEl) {
                    const offset = 80;
                    const top = targetEl.getBoundingClientRect().top + window.scrollY - offset;
                    window.scrollTo({ top, behavior: 'smooth' });
                }
            });
        });
    </script>
</body>
</html>
```
