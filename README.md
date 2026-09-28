<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tu Próximo Perfume | E-commerce premium</title>
  <meta name="description" content="Catálogo premium de perfumes con carrito, filtros, búsqueda y checkout." />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet" />
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet" />
  <style>
    :root {
      --bg: #f7f2ed;
      --bg-soft: #f0e7de;
      --card: #fffdfb;
      --primary: #171312;
      --primary-2: #2a2525;
      --gold: #cda75a;
      --gold-strong: #b98a28;
      --gold-soft: rgba(205, 167, 90, 0.12);
      --text: #221f1f;
      --muted: #665d5a;
      --border: #e7ddd3;
      --success: #2d7b5c;
      --danger: #d85e5e;
      --shadow: 0 25px 55px rgba(14, 12, 12, 0.10);
      --shadow-soft: 0 12px 26px rgba(14, 12, 12, 0.06);
      --radius: 20px;
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
    button, input, select { font: inherit; }
    h1, h2, h3, h4 { margin: 0; font-family: 'Cormorant Garamond', serif; letter-spacing: 0.02em; }

    .container {
      width: min(1200px, calc(100% - 30px));
      margin: 0 auto;
    }

    .topbar {
      background: var(--primary);
      color: rgba(255,255,255,0.9);
      text-align: center;
      font-size: 0.72rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      padding: 10px 12px;
      font-weight: 700;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 100;
      backdrop-filter: blur(10px);
      background: rgba(255, 253, 251, 0.9);
      border-bottom: 1px solid rgba(23, 19, 18, 0.06);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 22px;
      padding: 16px 0;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      color: var(--primary);
      text-transform: uppercase;
      letter-spacing: 0.08em;
      font-weight: 800;
      font-size: 0.93rem;
    }

    .brand i {
      color: var(--gold);
      font-size: 1.4rem;
    }

    .brand span { color: var(--gold); }

    nav {
      flex: 1;
      display: flex;
      justify-content: center;
    }

    .nav-links {
      list-style: none;
      display: flex;
      align-items: center;
      gap: 25px;
      margin: 0;
      padding: 0;
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
    .nav-links a.active::after { width: 100%; }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .search {
      display: flex;
      align-items: center;
      gap: 10px;
      background: white;
      border: 1px solid var(--border);
      border-radius: 999px;
      padding: 10px 14px;
      min-width: 220px;
      box-shadow: var(--shadow-soft);
    }

    .search i { color: var(--muted); }
    .search input {
      border: none;
      background: transparent;
      outline: none;
      width: 100%;
      color: var(--text);
    }

    .cart-button {
      position: relative;
      width: 46px;
      height: 46px;
      border-radius: 50%;
      border: 1px solid var(--border);
      background: white;
      color: var(--primary);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      box-shadow: var(--shadow-soft);
      transition: transform 0.2s ease;
    }

    .cart-button:hover { transform: translateY(-2px); }

    .cart-count {
      position: absolute;
      top: -5px;
      right: -4px;
      background: var(--gold);
      color: white;
      min-width: 20px;
      height: 20px;
      padding: 0 5px;
      border-radius: 50%;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-size: 0.7rem;
      font-weight: 800;
    }

    .hero {
      position: relative;
      min-height: 560px;
      display: flex;
      align-items: center;
      background:
        linear-gradient(rgba(17, 14, 14, 0.57), rgba(17, 14, 14, 0.55)),
        url('https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&q=80&w=1800') center/cover no-repeat;
      color: white;
      overflow: hidden;
    }

    .hero::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at top right, rgba(205, 167, 90, 0.18), transparent 35%);
    }

    .hero-inner {
      position: relative;
      width: min(1200px, calc(100% - 30px));
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap: 40px;
      align-items: center;
      padding: 60px 0;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 18px;
      font-size: 0.75rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: rgba(255,255,255,0.8);
      font-weight: 700;
    }

    .eyebrow .dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--gold);
      box-shadow: 0 0 14px rgba(205, 167, 90, 0.7);
    }

    .hero h1 {
      font-size: clamp(3rem, 5vw, 5.2rem);
      line-height: 0.95;
      font-weight: 600;
      margin-bottom: 16px;
      color: white;
    }

    .hero p {
      margin: 0 0 28px;
      max-width: 640px;
      font-size: 1.08rem;
      color: rgba(255,255,255,0.82);
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
      gap: 8px;
      padding: 14px 26px;
      border-radius: 999px;
      border: 1px solid transparent;
      cursor: pointer;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      font-size: 0.78rem;
      font-weight: 800;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .btn:hover { transform: translateY(-2px); }

    .btn-primary {
      background: var(--gold);
      color: white;
      box-shadow: 0 20px 30px rgba(205, 167, 90, 0.28);
    }

    .btn-secondary {
      background: rgba(255,255,255,0.06);
      color: white;
      border-color: rgba(255,255,255,0.18);
    }

    .hero-card {
      width: min(420px, 100%);
      justify-self: end;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(255,255,255,0.14);
      backdrop-filter: blur(10px);
      border-radius: 28px;
      padding: 22px;
      box-shadow: 0 26px 60px rgba(0,0,0,0.15);
    }

    .hero-card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 14px;
      margin-bottom: 20px;
      color: rgba(255,255,255,0.8);
      font-size: 0.72rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      font-weight: 700;
    }

    .mini-badge {
      border: 1px solid rgba(205, 167, 90, 0.5);
      background: rgba(205, 167, 90, 0.15);
      color: white;
      border-radius: 999px;
      padding: 8px 12px;
      font-size: 0.7rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .featured-product {
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: 22px;
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
      align-items: center;
      justify-content: space-between;
      gap: 16px;
    }

    .featured-meta h3 {
      font-size: 2rem;
      color: white;
      line-height: 1;
    }

    .featured-price {
      font-size: 1.35rem;
      color: var(--gold);
      font-weight: 800;
      font-family: 'Inter', sans-serif;
    }

    .featured-notes {
      margin-top: 10px;
      color: rgba(255,255,255,0.8);
      font-size: 0.9rem;
      font-family: 'Inter', sans-serif;
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
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 16px 18px;
      background: linear-gradient(180deg, #fff, #fffaf7);
      border: 1px solid var(--border);
      border-radius: 16px;
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
      font-size: 1.1rem;
    }

    .feature-box h4 {
      font-size: 1.18rem;
      color: var(--primary);
      margin-bottom: 4px;
    }

    .feature-box p {
      margin: 0;
      color: var(--muted);
      font-size: 0.82rem;
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
      font-size: clamp(2.5rem, 4vw, 3.5rem);
      color: var(--primary);
      line-height: 1;
    }

    .section-head p {
      max-width: 520px;
      margin: 0;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
    }

    .category-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 20px;
      margin: 30px 0 48px;
    }

    .category-card {
      position: relative;
      min-height: 230px;
      display: flex;
      align-items: end;
      padding: 20px;
      overflow: hidden;
      border-radius: 24px;
      color: white;
      background-size: cover;
      background-position: center;
      box-shadow: var(--shadow-soft);
    }

    .category-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(180deg, rgba(17,14,14,0.1), rgba(17,14,14,0.74));
    }

    .category-card > * {
      position: relative;
      z-index: 1;
    }

    .category-card h3 {
      font-size: 2.3rem;
      line-height: 1;
      color: white;
      margin-bottom: 6px;
    }

    .category-card p {
      margin: 0;
      color: rgba(255,255,255,0.84);
      font-size: 0.9rem;
      font-family: 'Inter', sans-serif;
    }

    .catalog-controls {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 12px;
      margin: 24px auto 28px;
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
      color: white;
      border-color: var(--primary);
    }

    .toolbar-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 18px;
      flex-wrap: wrap;
      margin-bottom: 24px;
    }

    .sort-box {
      display: flex;
      align-items: center;
      gap: 10px;
      background: white;
      border: 1px solid var(--border);
      padding: 10px 14px;
      border-radius: 12px;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
    }

    .sort-box select {
      border: none;
      background: transparent;
      color: var(--text);
      outline: none;
      font-weight: 600;
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 24px;
    }

    .product-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 22px;
      overflow: hidden;
      box-shadow: var(--shadow-soft);
      transition: transform 0.25s ease, box-shadow 0.25s ease;
      cursor: pointer;
    }

    .product-card:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow);
    }

    .product-image {
      position: relative;
      height: 300px;
      background: #f5efe9;
      overflow: hidden;
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
      z-index: 2;
      background: var(--gold);
      color: white;
      border-radius: 999px;
      padding: 7px 10px;
      font-size: 0.68rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .product-body {
      display: flex;
      flex-direction: column;
      padding: 18px 18px 20px;
    }

    .product-category {
      font-size: 0.68rem;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      font-weight: 700;
      color: var(--muted);
      margin-bottom: 8px;
    }

    .product-body h3 {
      font-size: 2rem;
      line-height: 1;
      color: var(--primary);
      margin-bottom: 10px;
    }

    .product-notes {
      min-height: 70px;
      font-size: 0.9rem;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
      margin-bottom: 18px;
    }

    .product-footer {
      margin-top: auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      padding-top: 14px;
      border-top: 1px solid rgba(23, 19, 18, 0.06);
    }

    .product-price {
      font-family: 'Inter', sans-serif;
      font-size: 1.4rem;
      font-weight: 800;
      color: var(--primary);
    }

    .add-btn {
      width: 46px;
      height: 46px;
      border-radius: 50%;
      border: none;
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
      margin-top: 18px;
      padding: 36px 20px;
      text-align: center;
      border: 1px dashed var(--border);
      border-radius: 18px;
      background: rgba(255,255,255,0.5);
      color: var(--muted);
      font-family: 'Inter', sans-serif;
    }

    .testimonials {
      margin-top: 92px;
    }

    .testimonial-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 20px;
      margin-top: 28px;
    }

    .testimonial-card {
      background: white;
      border: 1px solid var(--border);
      border-radius: 22px;
      padding: 22px;
      box-shadow: var(--shadow-soft);
    }

    .stars {
      color: var(--gold);
      letter-spacing: 0.12em;
      margin-bottom: 12px;
      font-size: 0.95rem;
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
      background: linear-gradient(135deg, var(--gold), #e8d8ab);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: 800;
    }

    .person strong {
      display: block;
      font-size: 0.95rem;
      margin-bottom: 0;
    }

    .person span {
      color: var(--muted);
      font-size: 0.8rem;
      font-family: 'Inter', sans-serif;
    }

    .cta-banner {
      margin-top: 72px;
      background: linear-gradient(135deg, #1b1a1a 0%, #2c2525 100%);
      border-radius: 26px;
      color: white;
      padding: 34px 30px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      box-shadow: var(--shadow);
    }

    .cta-banner h3 {
      font-size: clamp(2rem, 3vw, 2.9rem);
      line-height: 1;
      color: white;
      margin-bottom: 10px;
    }

    .cta-banner p {
      margin: 0;
      color: rgba(255,255,255,0.8);
      font-family: 'Inter', sans-serif;
    }

    footer {
      background: #130f0f;
      color: white;
      padding: 58px 0 22px;
      margin-top: 80px;
    }

    .footer-inner {
      display: grid;
      grid-template-columns: 1.2fr 1fr 1fr;
      gap: 28px;
      margin-bottom: 20px;
    }

    .footer-brand h3 {
      font-size: 2.5rem;
      color: white;
      margin-bottom: 10px;
    }

    .footer-brand p,
    .footer-col p,
    .footer-col a {
      color: rgba(255,255,255,0.72);
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
      margin: 0;
      padding: 0;
      display: grid;
      gap: 10px;
    }

    .footer-bottom {
      border-top: 1px solid rgba(255,255,255,0.08);
      padding-top: 18px;
      text-align: center;
      color: rgba(255,255,255,0.6);
      font-size: 0.8rem;
      font-family: 'Inter', sans-serif;
    }

    .modal {
      position: fixed;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
      background: rgba(0,0,0,0.62);
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.2s ease;
      z-index: 130;
    }

    .modal.open {
      opacity: 1;
      pointer-events: auto;
    }

    .modal-content {
      position: relative;
      width: min(760px, 100%);
      display: grid;
      grid-template-columns: 1fr 1fr;
      overflow: hidden;
      background: white;
      border-radius: 28px;
      box-shadow: 0 30px 80px rgba(0,0,0,0.2);
    }

    .modal-image {
      min-height: 420px;
      background: #f7efe9;
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
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 10px;
    }

    .modal-body h3 {
      font-size: 2.7rem;
      line-height: 1;
      color: var(--primary);
      margin-bottom: 10px;
    }

    .modal-body .desc {
      margin: 0 0 18px;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
      line-height: 1.7;
    }

    .modal-price-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 18px;
      margin: 8px 0 20px;
    }

    .modal-price {
      font-size: 2rem;
      font-weight: 800;
      color: var(--primary);
      font-family: 'Inter', sans-serif;
    }

    .close-modal {
      position: absolute;
      top: 16px;
      right: 16px;
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
      background: rgba(23, 19, 18, 0.96);
      color: white;
      border-radius: 12px;
      padding: 12px 16px;
      box-shadow: var(--shadow);
      opacity: 0;
      transform: translateY(12px);
      transition: opacity 0.25s ease, transform 0.25s ease;
      pointer-events: none;
      z-index: 200;
      font-family: 'Inter', sans-serif;
      font-size: 0.88rem;
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
      box-shadow: -18px 0 40px rgba(0,0,0,0.18);
      z-index: 120;
      transition: right 0.3s ease;
      display: flex;
      flex-direction: column;
    }

    .cart-drawer.open { right: 0; }

    .cart-header {
      background: var(--primary);
      padding: 22px 20px;
      color: white;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .cart-header h3 {
      font-size: 2.1rem;
      color: white;
      line-height: 1;
    }

    .close-cart {
      background: transparent;
      color: white;
      border: none;
      font-size: 1.4rem;
      cursor: pointer;
    }

    .cart-body {
      flex: 1;
      overflow-y: auto;
      padding: 18px;
      font-family: 'Inter', sans-serif;
    }

    .cart-item {
      display: flex;
      gap: 12px;
      align-items: center;
      border-bottom: 1px solid rgba(23,19,18,0.06);
      padding: 12px 0;
    }

    .cart-item img {
      width: 70px;
      height: 70px;
      object-fit: cover;
      border-radius: 12px;
    }

    .cart-item-info {
      flex: 1;
      min-width: 0;
    }

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
      color: var(--muted);
      margin-top: 8px;
      font-size: 0.8rem;
    }

    .qty-btn {
      width: 22px;
      height: 22px;
      border-radius: 50%;
      border: 1px solid var(--border);
      background: white;
      cursor: pointer;
      font-weight: 700;
      color: var(--primary);
    }

    .cart-item-remove {
      color: var(--danger);
      cursor: pointer;
      font-size: 1rem;
    }

    .cart-empty {
      text-align: center;
      color: var(--muted);
      padding-top: 38px;
      font-family: 'Inter', sans-serif;
    }

    .cart-footer {
      background: white;
      border-top: 1px solid rgba(23,19,18,0.08);
      padding: 18px;
    }

    .cart-total {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: 800;
      color: var(--primary);
      margin-bottom: 14px;
      font-size: 1.1rem;
    }

    .checkout-btn {
      width: 100%;
      padding: 14px 18px;
      border: none;
      border-radius: 14px;
      background: var(--gold);
      color: white;
      cursor: pointer;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .overlay {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.46);
      display: none;
      z-index: 99;
    }

    .overlay.open { display: block; }

    @media (max-width: 980px) {
      .hero-inner, .modal-content, .footer-inner {
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
        gap: 10px 16px;
      }

      .nav-actions {
        width: 100%;
        justify-content: space-between;
      }

      .search {
        min-width: 0;
        width: 100%;
      }

      .features-grid,
      .testimonial-grid,
      .category-grid {
        grid-template-columns: 1fr;
      }

      .section-head,
      .toolbar-row,
      .cta-banner {
        flex-direction: column;
        align-items: flex-start;
      }

      .hero-actions .btn {
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
        <label class="search" aria-label="Buscar">
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
      <div>
        <div class="eyebrow"><span class="dot"></span> Fragancias premium</div>
        <h1>Descubre la esencia que te define</h1>
        <p>Explora nuestra colección de perfumes premium para cada momento, estilo y personalidad. Firmeza, sofisticación y aroma inolvidable en cada botella.</p>
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
          <img src="https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&q=80&w=900" alt="Golden Muse" />
          <div class="featured-meta">
            <h3>Golden Muse</h3>
            <span class="featured-price">$160</span>
          </div>
          <div class="featured-notes">Jazmín, mango y vainilla dorada para una presencia memorable.</div>
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
          <p>Pagos protegidos</p>
        </div>
      </div>
      <div class="feature-box">
        <i class="fas fa-spa"></i>
        <div>
          <h4>Fórmulas premium</h4>
          <p>Notas exclusivas</p>
        </div>
      </div>
      <div class="feature-box">
        <i class="fas fa-gift"></i>
        <div>
          <h4>Regalos ideales</h4>
          <p>Presentación elegante</p>
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

      <div class="toolbar-row">
        <div></div>
        <label class="sort-box" aria-label="Ordenar producto">
          <span>Ordenar por</span>
          <select id="sortSelect">
            <option value="featured">Destacados</option>
            <option value="low">Precio: menor a mayor</option>
            <option value="high">Precio: mayor a menor</option>
            <option value="name">Nombre</option>
          </select>
        </label>
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
        <div class="modal-price-row">
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
      { id: 1, name: 'Elegance Noir', category: 'hombre', categoryText: 'Para Él', price: 120, badge: 'Más vendido', notes: 'Bergamota, pimienta negra y ámbar amaderado.', description: 'Una fragancia intensa y masculina con una base cálida de ámbar y maderas.', img: 'https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?auto=format&fit=crop&q=80&w=600' },
      { id: 2, name: 'Velvet Rose', category: 'mujer', categoryText: 'Para Ella', price: 145, badge: 'Nuevo', notes: 'Rosa de Damasco, vainilla y almizcle blanco.', description: 'Sensual y sofisticada con un toque floral intenso y final suave y elegante.', img: 'https://images.unsplash.com/photo-1592945403244-b3fbafd7f539?auto=format&fit=crop&q=80&w=600' },
      { id: 3, name: 'Citrus Breeze', category: 'unisex', categoryText: 'Unisex', price: 98, badge: '', notes: 'Limón siciliano, flor de azahar y cedro fresco.', description: 'Frescura vibrante y ligera para el día a día con un aire moderno y limpio.', img: 'https://images.unsplash.com/photo-1594035910387-fea47794261f?auto=format&fit=crop&q=80&w=600' },
      { id: 4, name: 'Midnight Oud', category: 'unisex', categoryText: 'Unisex / Nicho', price: 185, badge: 'Exclusivo', notes: 'Madera de oud, incienso, azafrán y cuero suave.', description: 'Una composición profunda y sofisticada con presencia nocturna y elegante.', img: 'https://images.unsplash.com/photo-1588405748880-12d1d2a59f75?auto=format&fit=crop&q=80&w=600' },
      { id: 5, name: 'Golden Muse', category: 'mujer', categoryText: 'Para Ella', price: 160, badge: 'Colección', notes: 'Jazmín, mango y vainilla dorada.', description: 'Radiant, cálida y muy femenina con un resultado glorioso y elegante.', img: 'https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&q=80&w=600' },
      { id: 6, name: 'Urban Scent', category: 'hombre', categoryText: 'Para Él', price: 110, badge: 'Top seller', notes: 'Nuez moscada, naranja amarga y sándalo elegante.', description: 'Un aroma moderno y refinado con carácter masculino y equilibrio perfecto.', img: 'https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&q=80&w=600' },
      { id: 7, name: 'Forest Bloom', category: 'unisex', categoryText: 'Unisex', price: 135, badge: 'Natural', notes: 'Loto, hojas verdes y musk blanco.', description: 'Aroma limpio y conectivo con un aire fresco urbanamente natural.', img: 'https://images.unsplash.com/photo-1563170351-be82bc888e1e?auto=format&fit=crop&q=80&w=600' },
      { id: 8, name: 'Amber Luxe', category: 'mujer', categoryText: 'Para Ella', price: 175, badge: 'Premium', notes: 'Ámbar, flor de naranjo y vainilla cálida.', description: 'Una fragancia cálida y envolvente que deja una impresión inolvidable.', img: 'https://images.unsplash.com/photo-1611078489935-0cb964de46d6?auto=format&fit=crop&q=80&w=600' },
      { id: 9, name: 'Noir Leather', category: 'hombre', categoryText: 'Para Él', price: 190, badge: 'Elite', notes: 'Cuero, tabaco y madera de cedro.', description: 'Fuerte, elegante y intenso para quienes buscan un perfume con carácter.', img: 'https://images.unsplash.com/photo-1523293182086-7651a899d37f?auto=format&fit=crop&q=80&w=600' },
      { id: 10, name: 'Bloom Silk', category: 'mujer', categoryText: 'Para Ella', price: 150, badge: 'Favorito', notes: 'Peonía, rosa y musk cremoso.', description: 'Romántica y sofisticada, con un estilo delicado y memorable.', img: 'https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&q=80&w=600' }
    ];

    const cartKey = 'tuproximo-cart';
    let cart = JSON.parse(localStorage.getItem(cartKey) || '[]');
    let currentFilter = 'all';
    let currentSort = 'featured';

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

    function sortProducts(items) {
      const list = [...items];
      switch (currentSort) {
        case 'low':
          return list.sort((a, b) => a.price - b.price);
        case 'high':
          return list.sort((a, b) => b.price - a.price);
        case 'name':
          return list.sort((a, b) => a.name.localeCompare(b.name));
        default:
          return list;
      }
    }

    function getFilteredProducts() {
      const searchValue = document.getElementById('searchInput').value.trim().toLowerCase();
      let filtered = products.filter(product => {
        const matchesCategory = currentFilter === 'all' || product.category === currentFilter;
        const matchesSearch = !searchValue || product.name.toLowerCase().includes(searchValue);
        return matchesCategory && matchesSearch;
      });
      return sortProducts(filtered);
    }

    function renderProducts() {
      const filtered = getFilteredProducts();
      const grid = document.getElementById('productsGrid');
      const empty = document.getElementById('emptyState');

      if (!filtered.length) {
        grid.innerHTML = '';
        empty.style.display = 'block';
        return;
      }

      empty.style.display = 'none';
      grid.innerHTML = filtered.map(product => `
        <article class="product-card" data-id="${product.id}">
          <div class="product-image">
            ${product.badge ? `<span class="product-badge">${product.badge}</span>` : ''}
            <img src="${product.img}" alt="${product.name}" />
          </div>
          <div class="product-body">
            <span class="product-category">${product.categoryText}</span>
            <h3>${product.name}</h3>
            <div class="product-notes">${product.notes}</div>
            <div class="product-footer">
              <span class="product-price">$${product.price.toFixed(2)}</span>
              <button class="add-btn" data-add-id="${product.id}" aria-label="Añadir ${product.name} al carrito">
                <i class="fas fa-bag-shopping"></i>
              </button>
            </div>
          </div>
        </article>
      `).join('');

      document.querySelectorAll('.product-card').forEach(card => {
        card.addEventListener('click', event => {
          if (event.target.closest('.add-btn')) return;
          const id = Number(card.dataset.id);
          openProductModal(id);
        });
      });

      document.querySelectorAll('.add-btn').forEach(button => {
        button.addEventListener('click', event => {
          event.stopPropagation();
          addToCart(Number(button.dataset.addId));
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
      document.getElementById('modalAddBtn').dataset.productId = product.id;
      document.getElementById('productModal').classList.add('open');
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
      const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
      document.getElementById('cartCount').textContent = totalItems;
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
    document.getElementById('sortSelect').addEventListener('change', (event) => {
      currentSort = event.target.value;
      renderProducts();
    });

    document.getElementById('cartToggle').addEventListener('click', openCart);
    document.getElementById('closeCart').addEventListener('click', closeCart);
    document.getElementById('overlay').addEventListener('click', closeCart);
    document.getElementById('closeModal').addEventListener('click', closeProductModal);
    document.getElementById('productModal').addEventListener('click', event => {
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
