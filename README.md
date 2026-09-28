<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tu Próximo Perfume</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --primary: #171717;
            --primary-soft: #2d2d2d;
            --accent: #d4af37;
            --accent-hover: #b9901d;
            --bg-light: #f7f4ef;
            --card-bg: #ffffff;
            --text-dark: #2a2a2a;
            --text-muted: #6e6e6e;
            --border-color: #e9e1d4;
            --success: #2e8b57;
            --danger: #d95c5c;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
        }

        * { box-sizing: border-box; }

        html { scroll-behavior: smooth; }

        body {
            margin: 0;
            background: var(--bg-light);
            color: var(--text-dark);
            font-family: Georgia, 'Times New Roman', serif;
            line-height: 1.6;
        }

        a { text-decoration: none; }
        img { max-width: 100%; display: block; }
        button, input { font: inherit; }

        .top-bar {
            background: var(--primary);
            color: #fff;
            text-align: center;
            padding: 10px 20px;
            font-size: 0.8rem;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            font-family: Arial, sans-serif;
        }

        header {
            position: sticky;
            top: 0;
            z-index: 100;
            background: rgba(255,255,255,0.95);
            backdrop-filter: blur(8px);
            box-shadow: 0 2px 18px rgba(0,0,0,0.05);
        }

        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 18px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 20px;
        }

        .logo {
            display: inline-flex;
            align-items: center;
            gap: 12px;
            color: var(--primary);
            font-weight: 700;
            letter-spacing: 0.08em;
            text-transform: uppercase;
        }

        .logo i {
            color: var(--accent);
            font-size: 1.5rem;
        }

        .logo-text {
            font-size: 1.2rem;
        }

        .logo-text span {
            color: var(--accent);
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 24px;
            padding: 0;
            margin: 0;
        }

        nav a {
            color: var(--text-dark);
            font-family: Arial, sans-serif;
            font-size: 0.9rem;
            font-weight: 600;
            transition: color 0.2s ease;
        }

        nav a:hover,
        nav a.active {
            color: var(--accent);
        }

        .header-actions {
            display: flex;
            align-items: center;
            gap: 18px;
        }

        .cart-icon-wrapper {
            position: relative;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 42px;
            height: 42px;
            border-radius: 50%;
            cursor: pointer;
            color: var(--primary);
            transition: background 0.2s ease;
        }

        .cart-icon-wrapper:hover {
            background: rgba(212, 175, 55, 0.12);
        }

        .cart-count {
            position: absolute;
            top: -4px;
            right: -2px;
            min-width: 20px;
            height: 20px;
            padding: 0 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            background: var(--accent);
            color: #fff;
            font-size: 0.72rem;
            font-weight: 700;
            font-family: Arial, sans-serif;
        }

        .search-box {
            display: flex;
            align-items: center;
            background: #fff;
            border: 1px solid var(--border-color);
            border-radius: 999px;
            padding: 10px 16px;
            min-width: 260px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.02);
        }

        .search-box i {
            color: var(--text-muted);
            margin-right: 10px;
        }

        .search-box input {
            border: none;
            outline: none;
            width: 100%;
            background: transparent;
            color: var(--text-dark);
            font-family: Arial, sans-serif;
        }

        .hero {
            min-height: 520px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            background:
                linear-gradient(rgba(0,0,0,0.55), rgba(0,0,0,0.5)),
                url('https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&q=80&w=1600') center/cover no-repeat;
            padding: 40px 20px;
        }

        .hero-content {
            max-width: 780px;
        }

        .hero h1 {
            font-size: clamp(2.4rem, 4vw, 4rem);
            margin: 0 0 18px;
            font-weight: 400;
            letter-spacing: 2px;
        }

        .hero p {
            margin: 0 0 30px;
            font-family: Arial, sans-serif;
            font-size: 1.1rem;
            color: rgba(255,255,255,0.9);
        }

        .cta-row {
            display: flex;
            justify-content: center;
            gap: 16px;
            flex-wrap: wrap;
        }

        .btn-primary,
        .btn-secondary {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            border: none;
            border-radius: 2px;
            padding: 15px 32px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 0.8rem;
            font-weight: 700;
            font-family: Arial, sans-serif;
            transition: transform 0.2s ease, background 0.2s ease;
        }

        .btn-primary {
            background: var(--accent);
            color: white;
        }

        .btn-secondary {
            background: rgba(255,255,255,0.08);
            border: 1px solid rgba(255,255,255,0.4);
            color: white;
        }

        .btn-primary:hover,
        .btn-secondary:hover {
            transform: translateY(-2px);
        }

        .main-container {
            max-width: 1200px;
            margin: 60px auto;
            padding: 0 20px;
        }

        .section-title {
            text-align: center;
            margin-bottom: 28px;
        }

        .section-title h2 {
            display: inline-block;
            position: relative;
            margin: 0;
            font-size: clamp(2rem, 3vw, 3rem);
            color: var(--primary);
            padding-bottom: 16px;
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            left: 50%;
            bottom: 0;
            transform: translateX(-50%);
            width: 80px;
            height: 2px;
            background: var(--accent);
        }

        .toolbar {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            gap: 16px;
            margin: 30px 0 40px;
        }

        .filter-btn {
            background: white;
            border: 1px solid var(--border-color);
            border-radius: 999px;
            padding: 9px 22px;
            cursor: pointer;
            color: var(--text-dark);
            font-family: Arial, sans-serif;
            font-weight: 600;
            transition: all 0.2s ease;
        }

        .filter-btn:hover,
        .filter-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 28px;
        }

        .product-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.25s ease, box-shadow 0.25s ease;
            display: flex;
            flex-direction: column;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 14px 35px rgba(0,0,0,0.08);
        }

        .product-img-wrapper {
            position: relative;
            height: 270px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            background: #f8f6f2;
        }

        .product-img-wrapper img {
            width: 82%;
            height: 82%;
            object-fit: cover;
            border-radius: 8px;
            transition: transform 0.35s ease;
        }

        .product-card:hover .product-img-wrapper img {
            transform: scale(1.06);
        }

        .product-badge {
            position: absolute;
            top: 14px;
            left: 14px;
            z-index: 2;
            background: var(--accent);
            color: white;
            border-radius: 999px;
            padding: 5px 10px;
            font-size: 0.72rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-family: Arial, sans-serif;
        }

        .product-info {
            padding: 20px 18px 18px;
            display: flex;
            flex-direction: column;
            flex: 1;
        }

        .product-category {
            font-family: Arial, sans-serif;
            font-size: 0.72rem;
            font-weight: 700;
            letter-spacing: 1.8px;
            color: var(--text-muted);
            text-transform: uppercase;
            margin-bottom: 8px;
        }

        .product-name {
            margin: 0 0 10px;
            font-size: 1.35rem;
            color: var(--primary);
        }

        .product-notes {
            margin: 0 0 18px;
            color: var(--text-muted);
            font-family: Arial, sans-serif;
            font-size: 0.9rem;
            line-height: 1.6;
        }

        .product-footer {
            margin-top: auto;
            padding-top: 12px;
            border-top: 1px solid #f0ece6;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 15px;
        }

        .product-price {
            font-family: Arial, sans-serif;
            font-weight: 700;
            font-size: 1.35rem;
            color: var(--primary);
        }

        .add-to-cart-btn {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            border: none;
            background: var(--primary);
            color: white;
            cursor: pointer;
            transition: transform 0.2s ease, background 0.2s ease;
        }

        .add-to-cart-btn:hover {
            background: var(--accent);
            transform: scale(1.06);
        }

        .empty-state {
            display: none;
            text-align: center;
            color: var(--text-muted);
            font-family: Arial, sans-serif;
            background: rgba(255,255,255,0.7);
            border: 1px dashed var(--border-color);
            border-radius: 12px;
            padding: 30px;
            margin-top: 18px;
        }

        .cart-drawer {
            position: fixed;
            top: 0;
            right: -420px;
            width: min(100%, 390px);
            height: 100vh;
            background: white;
            box-shadow: -12px 0 35px rgba(0,0,0,0.15);
            z-index: 1000;
            display: flex;
            flex-direction: column;
            transition: right 0.3s ease;
        }

        .cart-drawer.open {
            right: 0;
        }

        .cart-header {
            background: var(--primary);
            color: white;
            padding: 20px 22px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .cart-header h3 {
            margin: 0;
            font-size: 1.65rem;
        }

        .close-cart {
            cursor: pointer;
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .cart-body {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
            font-family: Arial, sans-serif;
        }

        .cart-item {
            display: flex;
            gap: 14px;
            align-items: center;
            padding: 12px 0;
            border-bottom: 1px solid #f1efe9;
        }

        .cart-item img {
            width: 68px;
            height: 68px;
            object-fit: cover;
            border-radius: 8px;
        }

        .cart-item-details {
            flex: 1;
        }

        .cart-item-title {
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 3px;
        }

        .cart-item-price {
            color: var(--accent);
            font-weight: 700;
            font-size: 0.92rem;
        }

        .cart-item-qty {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            margin-top: 6px;
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .qty-btn {
            width: 20px;
            height: 20px;
            border: 1px solid var(--border-color);
            background: white;
            border-radius: 50%;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }

        .cart-item-remove {
            color: var(--danger);
            cursor: pointer;
            font-size: 1rem;
        }

        .cart-empty {
            text-align: center;
            color: var(--text-muted);
            padding-top: 36px;
            font-size: 0.95rem;
        }

        .cart-footer {
            background: #fff;
            border-top: 1px solid #f1efe9;
            padding: 20px;
            font-family: Arial, sans-serif;
        }

        .cart-total {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
            font-size: 1.1rem;
            font-weight: 700;
            color: var(--primary);
        }

        .checkout-btn {
            width: 100%;
            border: none;
            background: var(--accent);
            color: white;
            padding: 14px;
            border-radius: 4px;
            font-weight: 700;
            cursor: pointer;
            transition: background 0.2s ease;
        }

        .checkout-btn:hover {
            background: var(--accent-hover);
        }

        .overlay {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.45);
            z-index: 999;
            display: none;
        }

        .overlay.active {
            display: block;
        }

        footer {
            margin-top: 80px;
            background: var(--primary);
            color: #fff;
            padding: 50px 20px 30px;
            font-family: Arial, sans-serif;
        }

        .footer-container {
            max-width: 1200px;
            margin: 0 auto 40px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 28px;
        }

        .footer-col h4 {
            color: var(--accent);
            font-size: 1.1rem;
            margin-bottom: 16px;
            font-family: Georgia, 'Times New Roman', serif;
        }

        .footer-col p,
        .footer-col li,
        .footer-col a {
            color: #d7d7d7;
            font-size: 0.95rem;
        }

        .footer-col ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .footer-col li {
            margin-bottom: 10px;
        }

        .footer-bottom {
            max-width: 1200px;
            margin: 0 auto;
            border-top: 1px solid rgba(255,255,255,0.12);
            padding-top: 18px;
            text-align: center;
            color: #a9a9a9;
            font-size: 0.8rem;
        }

        @media (max-width: 900px) {
            .header-container {
                flex-wrap: wrap;
                justify-content: center;
            }

            nav {
                order: 3;
                width: 100%;
            }

            nav ul {
                justify-content: center;
                flex-wrap: wrap;
            }
        }

        @media (max-width: 640px) {
            .top-bar {
                font-size: 0.7rem;
                letter-spacing: 1px;
            }

            .search-box {
                min-width: 180px;
                width: 100%;
            }

            .hero {
                min-height: 440px;
            }

            .cta-row {
                flex-direction: column;
            }

            .btn-primary,
            .btn-secondary {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="top-bar">Envío gratis en pedidos superiores a $50.000 • 3 cuotas sin interés</div>

    <header>
        <div class="header-container">
            <a href="#" class="logo" aria-label="inicio">
                <i class="fas fa-spray-can"></i>
                <div class="logo-text">Tu Próximo <span>Perfume</span></div>
            </a>

            <nav aria-label="Navegación principal">
                <ul>
                    <li><a href="#" class="active">Inicio</a></li>
                    <li><a href="#catalogo">Catálogo</a></li>
                    <li><a href="#hombre">Hombre</a></li>
                    <li><a href="#mujer">Mujer</a></li>
                    <li><a href="#unisex">Unisex</a></li>
                </ul>
            </nav>

            <div class="header-actions">
                <div class="search-box" aria-label="Buscar perfumes">
                    <i class="fas fa-search"></i>
                    <input type="text" id="searchInput" placeholder="Buscar perfum..." aria-label="Buscar perfume">
                </div>
                <div class="cart-icon-wrapper" id="cartToggle" aria-label="Abrir carrito">
                    <i class="fas fa-shopping-bag"></i>
                    <span class="cart-count" id="cartCount">0</span>
                </div>
            </div>
        </div>
    </header>

    <section class="hero">
        <div class="hero-content">
            <h1>Descubre la esencia que te define</h1>
            <p>Explora nuestra colección premium de fragancias internacionales y encuentra el aroma perfecto para cada momento.</p>
            <div class="cta-row">
                <a href="#catalogo" class="btn-primary">Ver catálogo</a>
                <a href="#hombre" class="btn-secondary">Lo más vendido</a>
            </div>
        </div>
    </section>

    <main class="main-container" id="catalogo">
        <div class="section-title">
            <h2>Nuestra Colección</h2>
        </div>

        <div class="toolbar">
            <button class="filter-btn active" data-filter="all">Todos</button>
            <button class="filter-btn" data-filter="mujer">Para ella</button>
            <button class="filter-btn" data-filter="hombre">Para él</button>
            <button class="filter-btn" data-filter="unisex">Unisex</button>
        </div>

        <div id="productsGrid" class="products-grid"></div>
        <div id="emptyState" class="empty-state">No encontramos perfumes con ese nombre o categoría.</div>
    </main>

    <div class="cart-drawer" id="cartDrawer" aria-label="Carrito de compras">
        <div class="cart-header">
            <h3>Tu Carrito</h3>
            <span class="close-cart" id="closeCart" aria-label="Cerrar carrito"><i class="fas fa-times"></i></span>
        </div>
        <div class="cart-body" id="cartBody"></div>
        <div class="cart-footer">
            <div class="cart-total">
                <span>Total</span>
                <span id="cartTotal">$0.00</span>
            </div>
            <button class="checkout-btn" onclick="checkout()">Finalizar Compra</button>
        </div>
    </div>
    <div class="overlay" id="overlay"></div>

    <footer>
        <div class="footer-container">
            <div class="footer-col">
                <h4>Tu Próximo Perfume</h4>
                <p>Una experiencia olfativa premium para cada ocasión, estilo y personalidad.</p>
            </div>
            <div class="footer-col">
                <h4>Categorías</h4>
                <ul>
                    <li><a href="#">Perfumes de mujer</a></li>
                    <li><a href="#">Perfumes de hombre</a></li>
                    <li><a href="#">Fragancias unisex</a></li>
                </ul>
            </div>
            <div class="footer-col">
                <h4>Atención al cliente</h4>
                <ul>
                    <li><a href="#">Preguntas frecuentes</a></li>
                    <li><a href="#">Envíos y devoluciones</a></li>
                    <li><a href="#">Contacto</a></li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">© 2026 Tu Próximo Perfume. Todos los derechos reservados.</div>
    </footer>

    <script>
        const products = [
            {
                id: 1,
                name: 'Elegance Noir',
                category: 'hombre',
                categoryText: 'Para Él',
                price: 120.00,
                badge: 'Más vendido',
                notes: 'Bergamota, pimienta negra y ámbar amaderado.',
                img: 'https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?auto=format&fit=crop&q=80&w=600'
            },
            {
                id: 2,
                name: 'Velvet Rose',
                category: 'mujer',
                categoryText: 'Para Ella',
                price: 145.00,
                badge: 'Nuevo',
                notes: 'Rosa de Damasco, vainilla y almizcle blanco.',
                img: 'https://images.unsplash.com/photo-1592945403244-b3fbafd7f539?auto=format&fit=crop&q=80&w=600'
            },
            {
                id: 3,
                name: 'Citrus Breeze',
                category: 'unisex',
                categoryText: 'Unisex',
                price: 98.00,
                badge: '',
                notes: 'Limón siciliano, flor de azahar y cedro fresco.',
                img: 'https://images.unsplash.com/photo-1594035910387-fea47794261f?auto=format&fit=crop&q=80&w=600'
            },
            {
                id: 4,
                name: 'Midnight Oud',
                category: 'unisex',
                categoryText: 'Unisex / Nicho',
                price: 185.00,
                badge: 'Exclusivo',
                notes: 'Madera de oud, incienso, azafrán y cuero suave.',
                img: 'https://images.unsplash.com/photo-1588405748880-12d1d2a59f75?auto=format&fit=crop&q=80&w=600'
            },
            {
                id: 5,
                name: 'Golden Muse',
                category: 'mujer',
                categoryText: 'Para Ella',
                price: 160.00,
                badge: 'Colección',
                notes: 'Jazmín, mango y vainilla dorada para noches inolvidables.',
                img: 'https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&q=80&w=600'
            },
            {
                id: 6,
                name: 'Urban Scent',
                category: 'hombre',
                categoryText: 'Para Él',
                price: 110.00,
                badge: 'Top seller',
                notes: 'Nuez moscada, naranja amarga y sándalo elegante.',
                img: 'https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&q=80&w=600'
            },
            {
                id: 7,
                name: 'Forest Bloom',
                category: 'unisex',
                categoryText: 'Unisex',
                price: 135.00,
                badge: 'Natural',
                notes: 'Loto, hojas verdes y musk blanco con un aire limpio.',
                img: 'https://images.unsplash.com/photo-1563170351-be82bc888e1e?auto=format&fit=crop&q=80&w=600'
            },
            {
                id: 8,
                name: 'Amber Luxe',
                category: 'mujer',
                categoryText: 'Para Ella',
                price: 175.00,
                badge: 'Premium',
                notes: 'Ámbar, flor de naranjo y notas cálidas de vainilla.',
                img: 'https://images.unsplash.com/photo-1611078489935-0cb964de46d6?auto=format&fit=crop&q=80&w=600'
            }
        ];

        const cartKey = 'perfume-cart';
        let currentFilter = 'all';
        let cart = JSON.parse(localStorage.getItem(cartKey)) || [];

        function saveCart() {
            localStorage.setItem(cartKey, JSON.stringify(cart));
        }

        function renderProducts(items) {
            const grid = document.getElementById('productsGrid');
            const emptyState = document.getElementById('emptyState');

            if (!items.length) {
                grid.innerHTML = '';
                emptyState.style.display = 'block';
                return;
            }

            emptyState.style.display = 'none';
            grid.innerHTML = items.map(product => `
                <article class="product-card">
                    <div class="product-img-wrapper">
                        ${product.badge ? `<span class="product-badge">${product.badge}</span>` : ''}
                        <img src="${product.img}" alt="${product.name}">
                    </div>
                    <div class="product-info">
                        <span class="product-category">${product.categoryText}</span>
                        <h3 class="product-name">${product.name}</h3>
                        <p class="product-notes">${product.notes}</p>
                        <div class="product-footer">
                            <span class="product-price">$${product.price.toFixed(2)}</span>
                            <button class="add-to-cart-btn" onclick="addToCart(${product.id})" aria-label="Añadir ${product.name} al carrito">
                                <i class="fas fa-shopping-bag"></i>
                            </button>
                        </div>
                    </div>
                </article>
            `).join('');
        }

        function getVisibleProducts() {
            const searchValue = document.getElementById('searchInput').value.trim().toLowerCase();

            return products.filter(product => {
                const matchesCategory = currentFilter === 'all' || product.category === currentFilter;
                const matchesSearch = !searchValue || product.name.toLowerCase().includes(searchValue);
                return matchesCategory && matchesSearch;
            });
        }

        function updateCatalog() {
            renderProducts(getVisibleProducts());
        }

        function addToCart(productId) {
            const product = products.find(item => item.id === productId);
            if (!product) return;

            const itemInCart = cart.find(item => item.id === productId);
            if (itemInCart) {
                itemInCart.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }

            saveCart();
            updateCart();
            openCart();
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
            const cartCount = document.getElementById('cartCount');
            const cartBody = document.getElementById('cartBody');
            const cartTotal = document.getElementById('cartTotal');

            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;

            if (!cart.length) {
                cartBody.innerHTML = '<p class="cart-empty">Tu carrito está vacío</p>';
                cartTotal.textContent = '$0.00';
                return;
            }

            let total = 0;
            cartBody.innerHTML = cart.map(item => {
                total += item.price * item.quantity;
                return `
                    <div class="cart-item">
                        <img src="${item.img}" alt="${item.name}">
                        <div class="cart-item-details">
                            <div class="cart-item-title">${item.name}</div>
                            <div class="cart-item-price">$${(item.price * item.quantity).toFixed(2)}</div>
                            <div class="cart-item-qty">
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

        function openCart() {
            document.getElementById('cartDrawer').classList.add('open');
            document.getElementById('overlay').classList.add('active');
        }

        function closeCart() {
            document.getElementById('cartDrawer').classList.remove('open');
            document.getElementById('overlay').classList.remove('active');
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

        document.querySelectorAll('.filter-btn').forEach(button => {
            button.addEventListener('click', () => {
                currentFilter = button.dataset.filter;
                document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.toggle('active', btn === button));
                updateCatalog();
            });
        });

        document.getElementById('cartToggle').addEventListener('click', openCart);
        document.getElementById('closeCart').addEventListener('click', closeCart);
        document.getElementById('overlay').addEventListener('click', closeCart);

        document.getElementById('searchInput').addEventListener('input', updateCatalog);

        renderProducts(products);
        updateCart();
    </script>
</body>
</html>
