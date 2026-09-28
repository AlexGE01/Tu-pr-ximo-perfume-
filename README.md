<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tu Próximo Perfume | Colección Premium</title>
  <meta name="description" content="Descubre fragancias premium para cada estilo y ocasión. Catálogo de perfumes de mujer, hombre y unisex." />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet" />
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet" />
  <style>
    :root {
      --bg: #f7f2eb;
      --bg-strong: #efe7dc;
      --card: #fffdfb;
      --primary: #171515;
      --primary-2: #2b2828;
      --gold: #c9a45c;
      --gold-strong: #b88936;
      --gold-soft: rgba(201, 164, 92, 0.12);
      --text: #252323;
      --muted: #695f5d;
      --border: #e6ddd1;
      --success: #2e7d5b;
      --shadow: 0 20px 50px rgba(23, 21, 21, 0.08);
      --shadow-soft: 0 10px 25px rgba(23, 21, 21, 0.06);
      --radius: 18px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      font-family: 'Inter', sans-serif;
      line-height: 1.6;
    }

    a { text-decoration: none; color: inherit; }
    img { display: block; max-width: 100%; }
    button, input { font: inherit; }
    h1, h2, h3, h4 { margin: 0; font-family: 'Cormorant Garamond', serif; letter-spacing: 0.02em; }

    .container {
      width: min(1200px, calc(100% - 32px));
      margin: 0 auto;
    }

    .topbar {
      background: var(--primary);
      color: white;
      font-size: 0.74rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      text-align: center;
      padding: 10px 16px;
      font-weight: 600;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 90;
      backdrop-filter: blur(10px);
      background: rgba(255, 253, 251, 0.9);
      border-bottom: 1px solid rgba(23, 21, 21, 0.05);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
      padding: 18px 0;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 12px;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--primary);
    }

    .brand i {
      color: var(--gold);
      font-size: 1.5rem;
    }

    .brand span {
      color: var(--gold);
    }

    nav {
      display: flex;
      justify-content: center;
      flex: 1;
    }

    .nav-links {
      list-style: none;
      display: flex;
      align-items: center;
      gap: 26px;
      padding: 0;
      margin: 0;
      font-weight: 600;
      color: var(--primary);
    }

    .nav-links a {
      position: relative;
      transition: color 0.2s ease;
    }

    .nav-links a::after {
      content: '';
      position: absolute;
      left: 0;
      bottom: -8px;
      width: 0;
      height: 2px;
      background: var(--gold);
      transition: width 0.25s ease;
    }

    .nav-links a:hover,
    .nav-links a.active {
      color: var(--gold-strong);
    }

    .nav-links a:hover::after,
    .nav-links a.active::after {
      width: 100%;
    }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .search {
      display: flex;
      align-items: center;
      gap: 10px;
      background: white;
      border: 1px solid var(--border);
      border-radius: 999px;
      min-width: 200px;
      padding: 10px 14px;
      box-shadow: var(--shadow-soft);
    }

    .search i { color: var(--muted); }
    .search input {
      border: none;
      outline: none;
      width: 100%;
      background: transparent;
      color: var(--text);
      font-size: 0.95rem;
    }

    .cart-button {
      position: relative;
      width: 46px;
      height: 46px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      border: 1px solid var(--border);
      border-radius: 50%;
      background: white;
      cursor: pointer;
      box-shadow: var(--shadow-soft);
      transition: transform 0.2s ease;
    }

    .cart-button:hover { transform: translateY(-2px); }

    .cart-count {
      position: absolute;
      top: -6px;
      right: -2px;
      min-width: 20px;
      height: 20px;
      padding: 0 5px;
      border-radius: 50%;
      background: var(--gold);
      color: white;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-size: 0.72rem;
      font-weight: 700;
    }

    .hero {
      position: relative;
      min-height: 560px;
      display: flex;
      align-items: center;
      background:
        linear-gradient(rgba(17, 14, 14, 0.58), rgba(17, 14, 14, 0.55)),
        url('https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&q=80&w=1800') center/cover no-repeat;
      color: white;
      overflow: hidden;
    }

    .hero::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at top right, rgba(201, 164, 92, 0.18), transparent 35%);
    }

    .hero-inner {
      position: relative;
      width: min(1200px, calc(100% - 32px));
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      align-items: center;
      gap: 40px;
      padding: 60px 0;
    }

    .hero-copy {
      max-width: 700px;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: rgba(255,255,255,0.82);
      font-size: 0.78rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      font-weight: 700;
      margin-bottom: 18px;
    }

    .eyebrow .dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--gold);
      box-shadow: 0 0 14px rgba(201, 164, 92, 0.75);
    }

    .hero h1 {
      font-size: clamp(3rem, 5vw, 5.2rem);
      line-height: 0.94;
      font-weight: 600;
      margin-bottom: 16px;
      color: #fff;
    }

    .hero p {
      font-size: 1.12rem;
      color: rgba(255,255,255,0.8);
      max-width: 600px;
      margin: 0 0 28px;
      font-family: 'Inter', sans-serif;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 16px;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 15px 28px;
      border-radius: 999px;
      border: 1px solid transparent;
      cursor: pointer;
      font-size: 0.8rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      transition: transform 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
    }

    .btn:hover { transform: translateY(-2px); }

    .btn-primary {
      background: var(--gold);
      color: white;
      box-shadow: 0 18px 30px rgba(201, 164, 92, 0.35);
    }

    .btn-secondary {
      background: rgba(255,255,255,0.06);
      color: white;
      border-color: rgba(255,255,255,0.18);
    }

    .hero-card {
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(255,255,255,0.12);
      backdrop-filter: blur(8px);
      border-radius: 28px;
      padding: 24px;
      box-shadow: 0 26px 60px rgba(0,0,0,0.18);
      justify-self: end;
      width: min(420px, 100%);
    }

    .hero-card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 22px;
      color: rgba(255,255,255,0.8);
      font-size: 0.76rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
    }

    .mini-badge {
      background: rgba(201, 164, 92, 0.2);
      color: white;
      border: 1px solid rgba(201, 164, 92, 0.4);
      border-radius: 999px;
      padding: 8px 12px;
      font-weight: 700;
      letter-spacing: 0.06em;
    }

    .featured-product {
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: 20px;
      padding: 16px;
    }

    .featured-product img {
      width: 100%;
      height: 280px;
      object-fit: cover;
      border-radius: 16px;
      margin-bottom: 18px;
    }

    .featured-meta {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      align-items: center;
    }

    .featured-meta h3 {
      font-size: 2rem;
      line-height: 1;
      color: white;
    }

    .featured-price {
      font-size: 1.3rem;
      font-weight: 700;
      color: var(--gold);
    }

    .featured-notes {
      font-size: 0.9rem;
      color: rgba(255,255,255,0.8);
      margin-top: 10px;
    }

    .features-strip {
      background: white;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      padding: 22px 0;
    }

    .features-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 18px;
    }

    .feature-box {
      padding: 16px 18px;
      display: flex;
      align-items: center;
      gap: 14px;
      border: 1px solid var(--border);
      border-radius: 16px;
      background: linear-gradient(180deg, #fff, #fffaf6);
      box-shadow: var(--shadow-soft);
    }

    .feature-box i {
      width: 46px;
      height: 46px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      background: var(--gold-soft);
      color: var(--gold-strong);
      font-size: 1.08rem;
    }

    .feature-box h4 {
      font-size: 1.2rem;
      color: var(--primary);
      margin-bottom: 4px;
    }

    .feature-box p {
      margin: 0;
      font-size: 0.82rem;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
    }

    main {
      padding: 80px 0 30px;
    }

    .section-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 20px;
      margin-bottom: 28px;
    }

    .section-head h2 {
      font-size: clamp(2.4rem, 4vw, 3.3rem);
      color: var(--primary);
      line-height: 1;
    }

    .section-head p {
      margin: 0;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
      max-width: 520px;
    }

    .category-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 20px;
      margin: 34px 0 50px;
    }

    .category-card {
      position: relative;
      overflow: hidden;
      border-radius: 24px;
      min-height: 230px;
      display: flex;
      align-items: end;
      padding: 20px;
      color: white;
      box-shadow: var(--shadow-soft);
      background-size: cover;
      background-position: center;
    }

    .category-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(180deg, rgba(17,14,14,0.12), rgba(17,14,14,0.78));
    }

    .category-card > * {
      position: relative;
      z-index: 1;
    }

    .category-card h3 {
      font-size: 2.2rem;
      margin: 0 0 4px;
      color: white;
    }

    .category-card p {
      margin: 0;
      color: rgba(255,255,255,0.82);
      font-size: 0.9rem;
      font-family: 'Inter', sans-serif;
    }

    .catalog-controls {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 12px;
      margin: 30px auto 26px;
    }

    .filter-btn {
      border: 1px solid var(--border);
      background: white;
      color: var(--text);
      padding: 10px 20px;
      border-radius: 999px;
      cursor: pointer;
      font-weight: 700;
      transition: all 0.2s ease;
    }

    .filter-btn.active,
    .filter-btn:hover {
      background: var(--primary);
      border-color: var(--primary);
      color: white;
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 26px;
      margin-top: 12px;
    }

    .product-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 22px;
      padding: 0;
      overflow: hidden;
      box-shadow: var(--shadow-soft);
      transition: transform 0.25s ease, box-shadow 0.25s ease;
    }

    .product-card:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow);
    }

    .product-image {
      position: relative;
      overflow: hidden;
      height: 300px;
      background: #f4efe8;
    }

    .product-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.35s ease;
    }

    .product-card:hover .product-image img { transform: scale(1.06); }

    .product-badge {
      position: absolute;
      top: 14px;
      left: 14px;
      padding: 7px 10px;
      border-radius: 999px;
      background: var(--gold);
      color: white;
      font-size: 0.7rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      z-index: 2;
    }

    .product-body {
      display: flex;
      flex-direction: column;
      padding: 18px 18px 20px;
    }

    .product-body .category {
      font-size: 0.7rem;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--muted);
      font-weight: 700;
      margin-bottom: 8px;
    }

    .product-body h3 {
      font-size: 2rem;
      line-height: 1;
      color: var(--primary);
      margin-bottom: 10px;
    }

    .notes {
      color: var(--muted);
      font-size: 0.9rem;
      font-family: 'Inter', sans-serif;
      margin-bottom: 18px;
      min-height: 70px;
    }

    .product-footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      margin-top: auto;
      padding-top: 14px;
      border-top: 1px solid rgba(23,21,21,0.06);
    }

    .price {
      font-size: 1.35rem;
      font-weight: 800;
      color: var(--primary);
      font-family: 'Inter', sans-serif;
    }

    .add-btn {
      width: 46px;
      height: 46px;
      border: none;
      border-radius: 50%;
      background: var(--primary);
      color: white;
      cursor: pointer;
      transition: background 0.2s ease, transform 0.2s ease;
    }

    .add-btn:hover {
      background: var(--gold);
      transform: scale(1.04);
    }

    .empty-state {
      display: none;
      text-align: center;
      padding: 38px 20px;
      border: 1px dashed var(--border);
      border-radius: 18px;
      background: rgba(255,255,255,0.55);
      color: var(--muted);
      font-family: 'Inter', sans-serif;
      margin-top: 18px;
    }

    .testimonials {
      margin-top: 80px;
      padding: 26px 0 30px;
    }

    .testimonial-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 20px;
      margin-top: 30px;
    }

    .testimonial-card {
      background: white;
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 22px;
      box-shadow: var(--shadow-soft);
    }

    .stars {
      color: var(--gold);
      margin-bottom: 12px;
      letter-spacing: 0.12em;
      font-size: 0.9rem;
    }

    .testimonial-card p {
      margin: 0 0 18px;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
    }

    .person {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .person-avatar {
      width: 42px;
      height: 42px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--gold), #e5cc95);
      color: white;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-weight: 800;
    }

    .person strong {
      display: block;
      font-size: 0.95rem;
    }

    .person span {
      color: var(--muted);
      font-size: 0.8rem;
      font-family: 'Inter', sans-serif;
    }

    .cta-banner {
      background: linear-gradient(135deg, #1a1919 0%, #282221 100%);
      color: white;
      border-radius: 26px;
      padding: 38px 30px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      margin-top: 70px;
      box-shadow: var(--shadow);
    }

    .cta-banner h3 {
      font-size: clamp(2rem, 3vw, 3rem);
      color: white;
      margin-bottom: 10px;
    }

    .cta-banner p {
      margin: 0;
      color: rgba(255,255,255,0.8);
      font-family: 'Inter', sans-serif;
    }

    footer {
      background: #120f0f;
      color: white;
      padding: 50px 0 24px;
      margin-top: 80px;
    }

    .footer-inner {
      display: grid;
      grid-template-columns: 1.3fr 1fr 1fr;
      gap: 28px;
      margin-bottom: 24px;
    }

    .footer-brand h3 {
      font-size: 2.3rem;
      color: white;
      margin-bottom: 10px;
    }

    .footer-brand p,
    .footer-col p,
    .footer-col a {
      color: rgba(255,255,255,0.7);
      font-family: 'Inter', sans-serif;
      line-height: 1.7;
    }

    .footer-col h4 {
      color: var(--gold);
      margin-bottom: 14px;
      font-size: 1.5rem;
    }

    .footer-col ul {
      list-style: none;
      padding: 0;
      margin: 0;
      display: grid;
      gap: 10px;
    }

    .footer-bottom {
      border-top: 1px solid rgba(255,255,255,0.08);
      padding-top: 20px;
      text-align: center;
      color: rgba(255,255,255,0.6);
      font-size: 0.8rem;
      font-family: 'Inter', sans-serif;
    }

    .modal {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.6);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
      z-index: 120;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.2s ease;
    }

    .modal.open {
      opacity: 1;
      pointer-events: auto;
    }

    .modal-content {
      width: min(760px, 100%);
      background: white;
      border-radius: 28px;
      overflow: hidden;
      box-shadow: 0 30px 80px rgba(0,0,0,0.2);
      display: grid;
      grid-template-columns: 1fr 1fr;
    }

    .modal-image {
      background: #f7f0ea;
      min-height: 420px;
      overflow: hidden;
    }

    .modal-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .modal-body {
      padding: 26px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .modal-body .category {
      color: var(--muted);
      letter-spacing: 0.16em;
      text-transform: uppercase;
      font-size: 0.7rem;
      font-weight: 700;
      margin-bottom: 10px;
    }

    .modal-body h3 {
      font-size: 2.5rem;
      line-height: 1;
      color: var(--primary);
      margin-bottom: 10px;
    }

    .modal-body .desc {
      font-family: 'Inter', sans-serif;
      color: var(--muted);
      margin: 0 0 18px;
      line-height: 1.7;
    }

    .modal-body .price-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      margin: 10px 0 20px;
    }

    .modal-price {
      font-size: 2rem;
      font-weight: 800;
      color: var(--primary);
      font-family: 'Inter', sans-serif;
    }

    .modal-body .btn {
      width: 100%;
    }

    .close-modal {
      position: absolute;
      top: 16px;
      right: 18px;
      width: 42px;
      height: 42px;
      border-radius: 50%;
      border: 1px solid rgba(255,255,255,0.2);
      background: rgba(255,255,255,0.1);
      color: white;
      cursor: pointer;
      z-index: 2;
    }

    .toast {
      position: fixed;
      right: 22px;
      bottom: 22px;
      background: rgba(23,21,21,0.92);
      color: white;
      border-radius: 14px;
      padding: 12px 16px;
      box-shadow: var(--shadow);
      opacity: 0;
      transform: translateY(12px);
      transition: opacity 0.25s ease, transform 0.25s ease;
      pointer-events: none;
      z-index: 200;
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
    }

    .toast.show {
      opacity: 1;
      transform: translateY(0);
    }

    .cart-drawer {
      position: fixed;
      top: 0;
      right: -420px;
      width: min(100%, 390px);
      height: 100vh;
      background: white;
      box-shadow: -16px 0 40px rgba(0,0,0,0.18);
      z-index: 100;
      transition: right 0.3s ease;
      display: flex;
      flex-direction: column;
    }

    .cart-drawer.open { right: 0; }

    .cart-header {
      background: var(--primary);
      color: white;
      padding: 22px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .cart-header h3 {
      font-size: 2.1rem;
      color: white;
    }

    .close-cart {
      border: none;
      background: transparent;
      color: white;
      font-size: 1.4rem;
      cursor: pointer;
    }

    .cart-body {
      flex: 1;
      overflow-y: auto;
      padding: 18px 18px 0;
      font-family: 'Inter', sans-serif;
    }

    .cart-item {
      display: flex;
      gap: 14px;
      align-items: center;
      padding: 12px 0;
      border-bottom: 1px solid rgba(23,21,21,0.06);
    }

    .cart-item img {
      width: 70px;
      height: 70px;
      object-fit: cover;
      border-radius: 12px;
    }

    .cart-item-info { flex: 1; }

    .cart-item-name {
      font-weight: 700;
      color: var(--primary);
    }

    .cart-item-price {
      color: var(--gold-strong);
      font-weight: 700;
      margin-top: 4px;
      font-size: 0.94rem;
    }

    .qty-controls {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      margin-top: 8px;
      font-size: 0.8rem;
      color: var(--muted);
    }

    .qty-btn {
      width: 22px;
      height: 22px;
      border-radius: 50%;
      border: 1px solid var(--border);
      background: white;
      cursor: pointer;
      color: var(--primary);
      font-weight: 700;
    }

    .cart-item-remove {
      color: #d85a5a;
      cursor: pointer;
      font-size: 1rem;
    }

    .cart-empty {
      text-align: center;
      color: var(--muted);
      padding-top: 50px;
      font-family: 'Inter', sans-serif;
    }

    .cart-footer {
      border-top: 1px solid rgba(23,21,21,0.08);
      padding: 18px;
      background: white;
    }

    .cart-total {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 1.1rem;
      font-weight: 800;
      margin-bottom: 14px;
      color: var(--primary);
    }

    .checkout-btn {
      width: 100%;
      border: none;
      border-radius: 14px;
      background: var(--gold);
      color: white;
      padding: 14px 18px;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      cursor: pointer;
    }

    .overlay {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.48);
      display: none;
      z-index: 99;
    }

    .overlay.open { display: block; }

    @media (max-width: 980px) {
      .hero-inner,
      .modal-content,
      .footer-inner {
        grid-template-columns: 1fr;
      }

      .hero-card {
        justify-self: start;
      }

      .features-grid,
      .testimonial-grid,
      .category-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }

    @media (max-width: 740px) {
      .nav {
        flex-wrap: wrap;
        justify-content: center;
      }

      nav {
        width: 100%;
      }

      .nav-links {
        flex-wrap: wrap;
        gap: 14px 20px;
      }

      .search {
        min-width: 0;
        width: 100%;
      }

      .nav-actions {
        width: 100%;
        justify-content: space-between;
      }

      .features-grid,
      .category-grid,
      .testimonial-grid {
        grid-template-columns: 1fr;
      }

      .section-head,
      .cta-banner {
        flex-direction: column;
        align-items: flex-start;
      }

      .hero {
        min-height: 500px;
      }

      .hero-actions {
        flex-direction: column;
      }

      .btn {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <div class="topbar">Envío gratis en pedidos superiores a $50.000 • Hasta 3 cuotas sin interés</div>

  <header>
    <div class="container nav">
      <a href="#" class="brand" aria-label="Tu Próximo Perfume">
        <i class="fas fa-spray-can"></i>
        Tu Próximo <span>Perfume</span>
      </a>

      <nav aria-label="Navegación principal">
        <ul class="nav-links">
          <li><a href="#" class="active">Inicio</a></li>
          <li><a href="#catalogo">Catálogo</a></li>
          <li><a href="#colecciones">Colecciones</a></li>
          <li><a href="#opiniones">Opiniones</a></li>
        </ul>
      </nav>

      <div class="nav-actions">
        <label class="search" aria-label="Buscar perfume">
          <i class="fas fa-search"></i>
          <input id="searchInput" type="text" placeholder="Buscar perfume" />
        </label>
        <button class="cart-button" id="cartToggle" aria-label="Abrir carrito">
          <i class="fas fa-shopping-bag"></i>
          <span class="cart-count" id="cartCount">0</span>
        </button>
      </div>
    </div>
  </header>

  <section class="hero">
    <div class="hero-inner">
      <div class="hero-copy">
        <div class="eyebrow"><span class="dot"></span> Fragancias premium</div>
        <h1>Descubre la esencia que te define</h1>
        <p>En Tu Próximo Perfume encontrarás aromas elegantes, intensos y memorables para cada momento, estilo y personalidad.</p>
        <div class="hero-actions">
          <a href="#catalogo" class="btn btn-primary">Ver catálogo</a>
          <a href="#colecciones" class="btn btn-secondary">Colecciones</a>
        </div>
      </div>

      <div class="hero-card">
        <div class="hero-card-header">
          <span>Perfume destacado</span>
          <span class="mini-badge">Top seller</span>
        </div>
        <div class="featured-product">
          <img src="https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&q=80&w=900" alt="Perfume destacado" />
          <div class="featured-meta">
            <h3>Golden Muse</h3>
            <span class="featured-price">$160</span>
          </div>
          <div class="featured-notes">Jazmín, mango y vainilla dorada para una presencia inolvidable.</div>
        </div>
      </div>
    </div>
  </section>

  <div class="features-strip">
    <div class="container features-grid">
      <div class="feature-box">
        <i class="fas fa-truck-fast"></i>
        <div>
          <h4>Envío rápido</h4>
          <p>Entrega segura en todo el país</p>
        </div>
      </div>
      <div class="feature-box">
        <i class="fas fa-shield-halved"></i>
        <div>
          <h4>Compra segura</h4>
          <p>Pagos protegidos y confiables</p>
        </div>
      </div>
      <div class="feature-box">
        <i class="fas fa-spa"></i>
        <div>
          <h4>Fórmulas premium</h4>
          <p>Notas elegantes y exclusivas</p>
        </div>
      </div>
      <div class="feature-box">
        <i class="fas fa-gift"></i>
        <div>
          <h4>Regalos ideales</h4>
          <p>Presentaciones sofisticadas</p>
        </div>
      </div>
    </div>
  </div>

  <main>
    <div class="container">
      <div class="section-head">
        <h2>Descubre tus favoritos</h2>
        <p>Elegimos fragancias con aroma intenso, balance perfecto y una experiencia sensorial excepcional.</p>
      </div>

      <div class="category-grid" id="colecciones">
        <article class="category-card" style="background-image: url('https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&q=80&w=900');">
          <div>
            <h3>Para ella</h3>
            <p>Floral, sensual y sofisticado.</p>
          </div>
        </article>
        <article class="category-card" style="background-image: url('https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&q=80&w=900');">
          <div>
            <h3>Para él</h3>
            <p>Intenso, amaderado y elegante.</p>
          </div>
        </article>
        <article class="category-card" style="background-image: url('https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?auto=format&fit=crop&q=80&w=900');">
          <div>
            <h3>Unisex</h3>
            <p>Modernos y versátiles para todos.</p>
          </div>
        </article>
      </div>

      <div class="catalog-controls" id="catalogo">
        <button class="filter-btn active" data-filter="all">Todos</button>
        <button class="filter-btn" data-filter="mujer">Para ella</button>
        <button class="filter-btn" data-filter="hombre">Para él</button>
        <button class="filter-btn" data-filter="unisex">Unisex</button>
      </div>

      <div id="productsGrid" class="products-grid"></div>
      <div id="emptyState" class="empty-state">No encontramos perfumes con ese nombre o categoría.</div>

      <div class="testimonials" id="opiniones">
        <div class="section-head">
          <h2>Lo que dicen nuestras clientas y clientes</h2>
          <p>Calidad, elegancia y una experiencia de compra que se siente premium en cada detalle.</p>
        </div>

        <div class="testimonial-grid">
          <article class="testimonial-card">
            <div class="stars">★★★★★</div>
            <p>“La mejor experiencia de compra. El perfume llega impecable y el aroma dura todo el día. Me encantó.”</p>
            <div class="person">
              <div class="person-avatar">A</div>
              <div>
                <strong>Ana R.</strong>
                <span>Cliente premium</span>
              </div>
            </div>
          </article>

          <article class="testimonial-card">
            <div class="stars">★★★★★</div>
            <p>“Compré uno para regalo y quedó espectacular. La presentación es muy elegante y el aroma es increíble.”</p>
            <div class="person">
              <div class="person-avatar">J</div>
              <div>
                <strong>Javier M.</strong>
                <span>Cliente frecuente</span>
              </div>
            </div>
          </article>

          <article class="testimonial-card">
            <div class="stars">★★★★★</div>
            <p>“Me encanta la variedad de perfumes. Hay opciones para cada estilo, y el servicio fue excelente.”</p>
            <div class="person">
              <div class="person-avatar">C</div>
              <div>
                <strong>Catalina P.</strong>
                <span>Compradora online</span>
              </div>
            </div>
          </article>
        </div>
      </div>

      <div class="cta-banner">
        <div>
          <h3>Haz de cada día una experiencia inolvidable</h3>
          <p>Descubre perfumes que acompañan tu estilo, tus recuerdos y tus mejores momentos.</p>
        </div>
        <a href="#catalogo" class="btn btn-primary">Explorar ahora</a>
      </div>
    </div>
  </main>

  <footer>
    <div class="container footer-inner">
      <div class="footer-brand">
        <h3>Tu Próximo Perfume</h3>
        <p>Fragancias premium diseñadas para dejar huella con cada paso, cada gesto y cada momento especial.</p>
      </div>

      <div class="footer-col">
        <h4>Categorías</h4>
        <ul>
          <li><a href="#">Perfumes para ella</a></li>
          <li><a href="#">Perfumes para él</a></li>
          <li><a href="#">Fragancias unisex</a></li>
        </ul>
      </div>

      <div class="footer-col">
        <h4>Atención al cliente</h4>
        <ul>
          <li><a href="#">Envíos y devoluciones</a></li>
          <li><a href="#">Preguntas frecuentes</a></li>
          <li><a href="#">Contacto</a></li>
        </ul>
      </div>
    </div>

    <div class="container footer-bottom">© 2026 Tu Próximo Perfume. Todos los derechos reservados.</div>
  </footer>

  <div class="modal" id="productModal" aria-hidden="true">
    <button class="close-modal" id="closeModal" aria-label="Cerrar detalle"><i class="fas fa-times"></i></button>
    <div class="modal-content" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
      <div class="modal-image">
        <img id="modalImage" src="" alt="" />
      </div>
      <div class="modal-body">
        <div class="category" id="modalCategory">Perfume</div>
        <h3 id="modalTitle">Nombre</h3>
        <p class="desc" id="modalDesc"></p>
        <div class="price-row">
          <span class="modal-price" id="modalPrice">$0</span>
          <span class="mini-badge" id="modalBadge">Premium</span>
        </div>
        <button class="btn btn-primary" id="modalAddBtn">Añadir al carrito</button>
      </div>
    </div>
  </div>

  <div class="overlay" id="overlay"></div>

  <div class="cart-drawer" id="cartDrawer">
    <div class="cart-header">
      <h3>Tu carrito</h3>
      <button class="close-cart" id="closeCart" aria-label="Cerrar carrito"><i class="fas fa-times"></i></button>
    </div>
    <div class="cart-body" id="cartBody"></div>
    <div class="cart-footer">
      <div class="cart-total">
        <span>Total</span>
        <span id="cartTotal">$0.00</span>
      </div>
      <button class="checkout-btn" onclick="checkout()">Finalizar compra</button>
    </div>
  </div>

  <div class="toast" id="toast">Añadido al carrito</div>

  <script>
    const products = [
      {
        id: 1,
        name: 'Elegance Noir',
        category: 'hombre',
        categoryText: 'Para Él',
        price: 120,
        badge: 'Más vendido',
        notes: 'Bergamota, pimienta negra y ámbar amaderado.',
        description: 'Una fragancia intensa y masculina, marcada por un equilibrio perfecto entre frescura cítrica y calidez de ámbar y madera.',
        img: 'https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 2,
        name: 'Velvet Rose',
        category: 'mujer',
        categoryText: 'Para Ella',
        price: 145,
        badge: 'Nuevo',
        notes: 'Rosa de Damasco, vainilla y almizcle blanco.',
        description: 'Seductora y elegante, con una salida floral envolvente y un fondo suave y adictivo que la hace inolvidable.',
        img: 'https://images.unsplash.com/photo-1592945403244-b3fbafd7f539?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 3,
        name: 'Citrus Breeze',
        category: 'unisex',
        categoryText: 'Unisex',
        price: 98,
        badge: '',
        notes: 'Limón siciliano, flor de azahar y cedro fresco.',
        description: 'Una propuesta fresca y ligera ideal para el día a día, con una sensación limpia, vibrante y siempre moderna.',
        img: 'https://images.unsplash.com/photo-1594035910387-fea47794261f?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 4,
        name: 'Midnight Oud',
        category: 'unisex',
        categoryText: 'Unisex / Nicho',
        price: 185,
        badge: 'Exclusivo',
        notes: 'Madera de oud, incienso, azafrán y cuero suave.',
        description: 'Una interpretación profunda y sofisticada para quienes buscan una fragancia intensa, cremosa y muy distintiva.',
        img: 'https://images.unsplash.com/photo-1588405748880-12d1d2a59f75?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 5,
        name: 'Golden Muse',
        category: 'mujer',
        categoryText: 'Para Ella',
        price: 160,
        badge: 'Colección',
        notes: 'Jazmín, mango y vainilla dorada.',
        description: 'Radiant, cálida y sofisticada, con una capa floral tropical que se convierte en un recuerdo elegante y duradero.',
        img: 'https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 6,
        name: 'Urban Scent',
        category: 'hombre',
        categoryText: 'Para Él',
        price: 110,
        badge: 'Top seller',
        notes: 'Nuez moscada, naranja amarga y sándalo elegante.',
        description: 'Una fragancia moderna con personalidad, que combina un inicio cítrico vibrante con un fondo amaderado muy refinado.',
        img: 'https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 7,
        name: 'Forest Bloom',
        category: 'unisex',
        categoryText: 'Unisex',
        price: 135,
        badge: 'Natural',
        notes: 'Loto, hojas verdes y musk blanco.',
        description: 'Una composición fresca y reconfortante con un aire limpio y muy contemporáneo, ideal para la vida diaria.',
        img: 'https://images.unsplash.com/photo-1563170351-be82bc888e1e?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 8,
        name: 'Amber Luxe',
        category: 'mujer',
        categoryText: 'Para Ella',
        price: 175,
        badge: 'Premium',
        notes: 'Ámbar, flor de naranjo y vainilla cálida.',
        description: 'Una versatilidad elegante con un fondo cálido y envolvente, diseñada para quienes desean dejar una huella memorable.',
        img: 'https://images.unsplash.com/photo-1611078489935-0cb964de46d6?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 9,
        name: 'Noir Leather',
        category: 'hombre',
        categoryText: 'Para Él',
        price: 190,
        badge: 'Elite',
        notes: 'Cuero, tabaco y madera de cedro.',
        description: 'Una fragancia sofisticada con presencia imponente, ideal para eventos nocturnos y looks con personalidad fuerte.',
        img: 'https://images.unsplash.com/photo-1523293182086-7651a899d37f?auto=format&fit=crop&q=80&w=600'
      },
      {
        id: 10,
        name: 'Bloom Silk',
        category: 'mujer',
        categoryText: 'Para Ella',
        price: 150,
        badge: 'Favorito',
        notes: 'Peonía, rosa y musk cremoso.',
        description: 'Un aroma suave, romántico y sofisticado que resalta la femineidad con un toque suave y muy elegante.',
        img: 'https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&q=80&w=600'
      }
    ];

    const cartKey = 'tuproximo-cart';
    let cart = JSON.parse(localStorage.getItem(cartKey) || '[]');
    let currentFilter = 'all';

    function saveCart() {
      localStorage.setItem(cartKey, JSON.stringify(cart));
    }

    function showToast(message) {
      const toast = document.getElementById('toast');
      toast.textContent = message;
      toast.classList.add('show');
      clearTimeout(showToast.timer);
      showToast.timer = setTimeout(() => toast.classList.remove('show'), 1800);
    }

    function getFilteredProducts() {
      const searchValue = document.getElementById('searchInput').value.trim().toLowerCase();

      return products.filter(product => {
        const matchesCategory = currentFilter === 'all' || product.category === currentFilter;
        const matchesSearch = !searchValue || product.name.toLowerCase().includes(searchValue);
        return matchesCategory && matchesSearch;
      });
    }

    function renderProducts() {
      const filteredProducts = getFilteredProducts();
      const grid = document.getElementById('productsGrid');
      const emptyState = document.getElementById('emptyState');

      if (!filteredProducts.length) {
        grid.innerHTML = '';
        emptyState.style.display = 'block';
        return;
      }

      emptyState.style.display = 'none';
      grid.innerHTML = filteredProducts.map(product => `
        <article class="product-card" data-id="${product.id}">
          <div class="product-image">
            ${product.badge ? `<span class="product-badge">${product.badge}</span>` : ''}
            <img src="${product.img}" alt="${product.name}" />
          </div>
          <div class="product-body">
            <span class="category">${product.categoryText}</span>
            <h3>${product.name}</h3>
            <div class="notes">${product.notes}</div>
            <div class="product-footer">
              <span class="price">$${product.price.toFixed(2)}</span>
              <button class="add-btn" data-add-id="${product.id}" aria-label="Añadir ${product.name} al carrito">
                <i class="fas fa-bag-shopping"></i>
              </button>
            </div>
          </div>
        </article>
      `).join('');

      document.querySelectorAll('.product-card').forEach(card => {
        card.addEventListener('click', (event) => {
          if (event.target.closest('.add-btn')) return;
          const id = Number(card.dataset.id);
          openProductModal(id);
        });
      });

      document.querySelectorAll('.add-btn').forEach(button => {
        button.addEventListener('click', (event) => {
          event.stopPropagation();
          const productId = Number(button.dataset.addId);
          addToCart(productId);
        });
      });
    }

    function openProductModal(productId) {
      const product = products.find(item => item.id === productId);
      if (!product) return;

      document.getElementById('modalImage').src = product.img;
      document.getElementById('modalImage').alt = product.name;
      document.getElementById('modalCategory').textContent = product.categoryText;
      document.getElementById('modalTitle').textContent = product.name;
      document.getElementById('modalDesc').textContent = product.description;
      document.getElementById('modalPrice').textContent = `$${product.price.toFixed(2)}`;
      document.getElementById('modalBadge').textContent = product.badge || 'Premium';
      document.getElementById('productModal').classList.add('open');
      document.getElementById('modalAddBtn').dataset.productId = product.id;
    }

    function closeProductModal() {
      document.getElementById('productModal').classList.remove('open');
    }

    function addToCart(productId) {
      const product = products.find(item => item.id === productId);
      if (!product) return;

      const existing = cart.find(item => item.id === productId);
      if (existing) {
        existing.quantity += 1;
      } else {
        cart.push({ ...product, quantity: 1 });
      }

      saveCart();
      updateCart();
      showToast(`${product.name} añadido al carrito`);
      openCart();
      closeProductModal();
    }

    function updateQuantity(productId, delta) {
      const item = cart.find(entry => entry.id === productId);
      if (!item) return;

      item.quantity += delta;
      if (item.quantity <= 0) {
        cart = cart.filter(entry => entry.id !== productId);
      }

      saveCart();
      updateCart();
    }

    function removeFromCart(productId) {
      cart = cart.filter(item => item.id !== productId);
      saveCart();
      updateCart();
    }

    function updateCart() {
      const count = cart.reduce((sum, item) => sum + item.quantity, 0);
      document.getElementById('cartCount').textContent = count;

      const cartBody = document.getElementById('cartBody');
      const cartTotal = document.getElementById('cartTotal');

      if (!cart.length) {
        cartBody.innerHTML = '<div class="cart-empty">Tu carrito está vacío</div>';
        cartTotal.textContent = '$0.00';
        return;
      }

      let total = 0;
      cartBody.innerHTML = cart.map(item => {
        total += item.price * item.quantity;
        return `
          <div class="cart-item">
            <img src="${item.img}" alt="${item.name}" />
            <div class="cart-item-info">
              <div class="cart-item-name">${item.name}</div>
              <div class="cart-item-price">$${(item.price * item.quantity).toFixed(2)}</div>
              <div class="qty-controls">
                <button class="qty-btn" onclick="updateQuantity(${item.id}, -1)">-</button>
                <span>${item.quantity}</span>
                <button class="qty-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
              </div>
            </div>
            <i class="fas fa-trash cart-item-remove" onclick="removeFromCart(${item.id})" aria-label="Eliminar ${item.name}"></i>
          </div>
        `;
      }).join('');

      cartTotal.textContent = `$${total.toFixed(2)}`;
    }

    function checkout() {
      if (!cart.length) {
        alert('Tu carrito está vacío');
        return;
      }

      alert('¡Gracias por tu compra! Redirigiendo a la pasarela de pago...');
      cart = [];
      saveCart();
      updateCart();
      closeCart();
    }

    function openCart() {
      document.getElementById('cartDrawer').classList.add('open');
      document.getElementById('overlay').classList.add('open');
    }

    function closeCart() {
      document.getElementById('cartDrawer').classList.remove('open');
      document.getElementById('overlay').classList.remove('open');
    }

    document.querySelectorAll('.filter-btn').forEach(button => {
      button.addEventListener('click', () => {
        currentFilter = button.dataset.filter;
        document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.toggle('active', btn === button));
        renderProducts();
      });
    });

    document.getElementById('searchInput').addEventListener('input', renderProducts);

    document.getElementById('cartToggle').addEventListener('click', openCart);
    document.getElementById('closeCart').addEventListener('click', closeCart);
    document.getElementById('overlay').addEventListener('click', closeCart);
    document.getElementById('closeModal').addEventListener('click', closeProductModal);
    document.getElementById('productModal').addEventListener('click', (event) => {
      if (event.target === event.currentTarget) closeProductModal();
    });
    document.getElementById('modalAddBtn').addEventListener('click', () => {
      const id = Number(document.getElementById('modalAddBtn').dataset.productId);
      addToCart(id);
    });

    renderProducts();
    updateCart();
  </script>
</body>
</html>
