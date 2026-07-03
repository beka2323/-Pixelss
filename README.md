<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Уютный Дом | Пиксельный Мебельный Мир</title>
    <!-- Подключаем пиксельный шрифт для заголовков -->
    <link href="https://fonts.googleapis.com/css2?family=VT323&display=swap" rel="stylesheet">
    
    <style>
        /* =========================================
           БАЗОВЫЕ НАСТРОЙКИ И ПЕРЕМЕННЫЕ
        ========================================= */
        :root {
            --bg-color: #fcf8e3;
            --grid-color: #e5dfc5;
            --header-bg: #333;
            --accent-orange: #e67e22;
            --accent-blue: #4a86e8;
            --border-dark: #000;
            --text-dark: #000;
            --text-light: #fff;
            --font-pixel: 'VT323', monospace;
            --font-base: 'Courier New', Courier, monospace;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            background-image: 
                linear-gradient(90deg, var(--grid-color) 1px, transparent 1px),
                linear-gradient(var(--grid-color) 1px, transparent 1px);
            background-size: 20px 20px;
            color: var(--text-dark);
            font-family: var(--font-base);
            position: relative;
        }

        /* Эффект старого телевизора (CRT scanlines) */
        body::before {
            content: " ";
            display: block;
            position: absolute;
            top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.05) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.03), rgba(0, 255, 0, 0.01), rgba(0, 0, 255, 0.03));
            z-index: 9999;
            background-size: 100% 4px, 6px 100%;
            pointer-events: none;
            position: fixed;
        }

        /* =========================================
           ШАПКА (HEADER)
        ========================================= */
        header {
            background-color: var(--header-bg);
            color: var(--text-light);
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 4px solid var(--border-dark);
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 4px 0 rgba(0,0,0,0.2);
        }

        .logo {
            font-family: var(--font-pixel);
            font-size: 2.8rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 3px 3px 0 var(--accent-orange);
        }

        .header-right {
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            gap: 10px;
        }

        .header-contacts {
            color: var(--accent-orange);
            font-size: 1.1rem;
            font-weight: bold;
            font-family: var(--font-pixel);
            letter-spacing: 1px;
        }
        
        .header-contacts a {
            color: var(--accent-orange);
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .header-contacts a:hover {
            color: #fff;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 20px;
        }

        nav a {
            color: var(--text-light);
            text-decoration: none;
            font-size: 1rem;
            font-weight: bold;
            text-transform: uppercase;
            cursor: pointer;
            padding: 5px;
            transition: all 0.2s;
        }

        nav a:hover, nav a.active {
            color: var(--accent-orange);
            background: rgba(255,255,255,0.1);
            border-radius: 2px;
        }

        /* =========================================
           БАННЕР И ПРЕИМУЩЕСТВА
        ========================================= */
        .hero {
            background-image: url('https://images.unsplash.com/photo-1550684848-fac1c5b4e853?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-position: center;
            height: 350px;
            display: flex;
            justify-content: center;
            align-items: center;
            border-bottom: 4px solid var(--border-dark);
        }

        .hero-overlay {
            background: rgba(20, 20, 20, 0.9);
            padding: 30px 40px;
            text-align: center;
            border: 4px solid var(--border-dark);
            box-shadow: 8px 8px 0 var(--border-dark);
            color: var(--text-light);
            max-width: 700px;
            transform: scale(0.95);
            animation: popIn 0.5s ease forwards;
        }

        @keyframes popIn {
            to { transform: scale(1); }
        }

        .hero h2 {
            font-family: var(--font-pixel);
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #fff;
            text-shadow: 2px 2px 0 var(--accent-orange);
        }

        .hero p {
            font-size: 1.1rem;
            line-height: 1.5;
            font-weight: bold;
        }

        .features-bar {
            background-color: var(--accent-blue);
            border-bottom: 4px solid var(--border-dark);
            padding: 20px 5%;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 30px;
        }

        .feature-item {
            border: 3px dashed #fff;
            padding: 10px 20px;
            color: white;
            font-weight: bold;
            font-size: 1.2rem;
            text-transform: uppercase;
            font-family: var(--font-pixel);
            letter-spacing: 1px;
            background: rgba(0,0,0,0.1);
        }

        /* =========================================
           КАТАЛОГ ТОВАРОВ
        ========================================= */
        .catalog {
            max-width: 1200px;
            margin: 40px auto;
            padding: 0 20px;
        }

        .catalog-title {
            text-align: center;
            font-family: var(--font-pixel);
            font-size: 3rem;
            margin-bottom: 40px;
            text-transform: uppercase;
            background: var(--bg-color);
            display: inline-block;
            padding: 0 20px;
            position: relative;
            left: 50%;
            transform: translateX(-50%);
            border-bottom: 4px solid var(--border-dark);
        }

        .catalog-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 40px 25px;
        }

        .category-block {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .category-name {
            font-weight: bold;
            font-size: 1.1rem;
            background: var(--bg-color);
            display: inline-block;
            padding: 2px 5px;
            border-left: 4px solid var(--border-dark);
        }

        /* Общие стили карточек */
        .card-wrapper {
            background: #fff;
            border: 3px solid var(--border-dark);
            box-shadow: 6px 6px 0px var(--border-dark);
            padding: 10px;
            transition: all 0.2s ease;
            position: relative;
        }

        .card-wrapper:hover {
            transform: translate(-3px, -3px);
            box-shadow: 9px 9px 0px var(--accent-orange);
        }

        /* Горизонтальная карточка (Стандарт) */
        .card-horizontal {
            display: flex;
            align-items: center;
            gap: 15px;
            height: 160px;
        }

        .card-horizontal img {
            width: 110px;
            height: 100%;
            object-fit: cover;
            border: 2px solid var(--border-dark);
        }

        .card-info {
            display: flex;
            flex-direction: column;
            justify-content: center;
            flex: 1;
        }

        .card-info strong {
            font-size: 1rem;
            line-height: 1.2;
            margin-bottom: 8px;
            height: 2.4em;
            overflow: hidden;
        }

        .card-info span {
            font-family: var(--font-pixel);
            font-size: 1.4rem;
            color: #c0392b;
            margin-bottom: 10px;
        }

        /* Двойная карточка (Как на скриншоте первая) */
        .card-double {
            display: flex;
            justify-content: space-between;
            gap: 10px;
            height: 160px;
        }

        .card-double-item {
            flex: 1;
            border: 2px solid var(--border-dark);
            height: 100%;
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }
        
        .card-double-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .card-double-item:hover img {
            transform: scale(1.1);
        }
        
        .card-double-item::after {
            content: "В КОРЗИНУ";
            position: absolute;
            bottom: 0; left: 0; right: 0;
            background: rgba(0,0,0,0.8);
            color: #fff;
            text-align: center;
            font-size: 0.8rem;
            padding: 5px 0;
            transform: translateY(100%);
            transition: transform 0.2s;
        }

        .card-double-item:hover::after {
            transform: translateY(0);
        }

        /* Кнопка покупки */
        .buy-btn {
            background: var(--border-dark);
            color: #fff;
            border: none;
            font-family: var(--font-pixel);
            font-size: 1.2rem;
            padding: 8px 5px;
            cursor: pointer;
            text-transform: uppercase;
            width: 100%;
            border-bottom: 3px solid #555;
        }

        .buy-btn:hover {
            background: var(--accent-orange);
            border-bottom-color: #ba6014;
        }
        
        .buy-btn:active {
            transform: translateY(2px);
            border-bottom-width: 1px;
        }

        /* =========================================
           ПОДВАЛ И КОНТАКТЫ
        ========================================= */
        .footer-contacts {
            text-align: center;
            margin: 60px auto 30px auto;
            max-width: 700px;
        }

        .footer-contacts-title {
            font-family: var(--font-base);
            font-weight: bold;
            font-size: 1.2rem;
            margin-bottom: 20px;
            background: var(--bg-color);
            display: inline-block;
            padding: 0 15px;
        }

        .footer-phone-box {
            background: #e6e6e6;
            border: 4px solid var(--border-dark);
            padding: 20px 30px;
            font-size: 3rem;
            font-weight: bold;
            font-family: var(--font-pixel);
            letter-spacing: 3px;
            box-shadow: inset 4px 4px 10px rgba(0,0,0,0.2), 8px 8px 0 var(--border-dark);
        }

        .copyright {
            text-align: center;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 20px 0 50px 0;
            background: var(--bg-color);
            border-top: 2px dashed #ccc;
            margin-top: 40px;
        }

        /* =========================================
           ВСПЛЫВАЮЩИЕ ОКНА (МОДАЛКИ)
        ========================================= */
        .modal {
            display: none; 
            position: fixed; 
            z-index: 10000; 
            left: 0; top: 0; 
            width: 100%; height: 100%; 
            background-color: rgba(0,0,0,0.85); 
            backdrop-filter: blur(3px);
        }

        .modal-content {
            background-color: var(--bg-color);
            margin: 5% auto; 
            padding: 30px;
            border: 6px solid var(--border-dark);
            box-shadow: 12px 12px 0px var(--accent-orange);
            max-width: 600px;
            width: 90%;
            position: relative;
            animation: slideDown 0.3s ease-out;
        }

        @keyframes slideDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .close-modal {
            position: absolute; 
            right: 15px; 
            top: 10px;
            font-size: 2.5rem; 
            cursor: pointer; 
            font-family: var(--font-pixel);
            color: #c0392b;
        }
        
        .close-modal:hover { color: #000; }

        .modal-title {
            font-family: var(--font-pixel);
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 20px;
            border-bottom: 4px dashed var(--border-dark);
            padding-bottom: 10px;
        }

        /* Стили внутри корзины */
        .cart-items-list {
            list-style: none; 
            margin: 20px 0; 
            max-height: 40pxvh; 
            overflow-y: auto;
            padding-right: 10px;
        }

        .cart-item {
            display: flex; 
            justify-content: space-between;
            align-items: center;
            padding: 15px 10px; 
            border-bottom: 2px dashed #aaa;
            background: #fff;
            margin-bottom: 10px;
            border: 2px solid var(--border-dark);
        }

        .cart-item-info {
            display: flex;
            flex-direction: column;
        }

        .cart-item-price {
            font-family: var(--font-pixel);
            font-size: 1.3rem;
            color: #c0392b;
        }

        .remove-btn {
            background: #e74c3c; 
            color: white; 
            border: 2px solid var(--border-dark);
            cursor: pointer; 
            padding: 5px 10px; 
            font-weight: bold;
            font-family: var(--font-pixel);
            font-size: 1.2rem;
            box-shadow: 2px 2px 0 #000;
        }
        
        .remove-btn:hover { background: #c0392b; transform: translate(1px, 1px); box-shadow: 1px 1px 0 #000;}

        .cart-total {
            font-size: 1.5rem; 
            font-weight: bold; 
            text-align: right; 
            margin-top: 20px;
            font-family: var(--font-pixel);
        }

        .whatsapp-btn {
            display: block; 
            text-align: center; 
            background: #27ae60; 
            color: white;
            text-decoration: none; 
            padding: 15px; 
            font-family: var(--font-pixel);
            font-size: 1.8rem;
            border: 4px solid var(--border-dark); 
            margin-top: 25px; 
            box-shadow: 6px 6px 0 var(--border-dark);
            transition: all 0.2s;
        }

        .whatsapp-btn:hover { 
            background: #2ecc71; 
            transform: translate(-2px, -2px);
            box-shadow: 8px 8px 0 var(--accent-orange);
        }

        /* =========================================
           УВЕДОМЛЕНИЯ (ТОСТЫ)
        ========================================= */
        #toast-container {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 10001;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .toast {
            background: var(--bg-color);
            border: 3px solid var(--border-dark);
            box-shadow: 5px 5px 0 var(--border-dark);
            padding: 15px 20px;
            font-weight: bold;
            font-family: var(--font-base);
            display: flex;
            align-items: center;
            gap: 10px;
            animation: slideInRight 0.3s ease-out forwards, fadeOut 0.5s ease-out 2.5s forwards;
        }

        .toast-icon {
            font-size: 1.5rem;
        }

        @keyframes slideInRight {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        @keyframes fadeOut {
            from { opacity: 1; }
            to { opacity: 0; display: none; }
        }

        /* =========================================
           АДАПТИВНОСТЬ (МЕДИА ЗАПРОСЫ)
        ========================================= */
        @media (max-width: 1024px) {
            .catalog-grid { grid-template-columns: repeat(2, 1fr); }
            header { flex-direction: column; gap: 15px; }
            .header-right { align-items: center; }
        }

        @media (max-width: 768px) {
            .catalog-grid { grid-template-columns: 1fr; }
            .features-bar { flex-direction: column; align-items: center; text-align: center; }
            .hero h2 { font-size: 2rem; }
            .footer-phone-box { font-size: 2rem; padding: 15px; }
            .logo { font-size: 2.2rem; }
        }
    </style>
</head>
<body>

    <!-- ШАПКА -->
    <header>
        <div class="logo">УЮТНЫЙ ДОМ</div>
        <div class="header-right">
            <div class="header-contacts">
                📞 ТЕЛИК/WA: <a href="tel:+996553548008">+996 553 548 008</a>
            </div>
            <nav>
                <ul>
                    <li><a href="#" class="active">ГЛАВНАЯ</a></li>
                    <li><a href="#catalog">КАТАЛОГ</a></li>
                    <li><a onclick="openModal('promoModal')">АКЦИИ</a></li>
                    <li><a onclick="openModal('contactModal')">КОНТАКТЫ</a></li>
                    <li><a onclick="openModal('cartModal')" style="color: var(--accent-orange);">🛒 КОРЗИНА (<span id="cart-count">0</span>)</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- БАННЕР -->
    <section class="hero">
        <div class="hero-overlay">
            <h2>ПИКСЕЛЬНЫЙ МЕБЕЛЬНЫЙ МИР</h2>
            <p>Эксклюзивное качество, быстрая доставка и удобный заказ прямо в ваш мессенджер!</p>
        </div>
    </section>

    <!-- ПРЕИМУЩЕСТВА -->
    <div class="features-bar">
        <div class="feature-item">■ 100% НАДЕЖНО</div>
        <div class="feature-item">■ КРУТЫЕ ФОТО</div>
        <div class="feature-item">■ ЗАКАЗ В WHATSAPP</div>
    </div>

    <!-- КАТАЛОГ -->
    <main class="catalog" id="catalog">
        <div class="catalog-title">КАТАЛОГ ТОВАРОВ</div>

        <div class="catalog-grid">
            
            <!-- Ряд 1, Колонка 1: Двойная карточка -->
            <div class="category-block">
                <div class="category-name">■ Мебель для дома (Общая)</div>
                <div class="card-wrapper card-double">
                    <div class="card-double-item" onclick="addToCart('Скандинавский диван', 45000)">
                        <img src="https://images.unsplash.com/photo-1555041469-a586c61ea9bc?auto=format&fit=crop&w=300&q=80" alt="Диван">
                    </div>
                    <div class="card-double-item" onclick="addToCart('Книжный стеллаж', 12900)">
                        <img src="https://images.unsplash.com/photo-1594620302200-9a762244a156?auto=format&fit=crop&w=300&q=80" alt="Стеллаж">
                    </div>
                </div>
            </div>

            <!-- Ряд 1, Колонка 2 -->
            <div class="category-block">
                <div class="category-name">■ Мебель для спальни</div>
                <div class="card-wrapper card-horizontal">
                    <img src="https://images.unsplash.com/photo-1505693314120-0d443867891c?auto=format&fit=crop&w=200&q=80" alt="Кровать">
                    <div class="card-info">
                        <strong>Двуспальная<br>кровать</strong>
                        <span>28500 сом</span>
                        <button class="buy-btn" onclick="addToCart('Двуспальная кровать', 28500)">В КОРЗИНУ</button>
                    </div>
                </div>
            </div>

            <!-- Ряд 1, Колонка 3 -->
            <div class="category-block">
                <div class="category-name">■ Мебель для ванной</div>
                <div class="card-wrapper card-horizontal">
                    <img src="https://images.unsplash.com/photo-1584622650111-993a426fbf0a?auto=format&fit=crop&w=200&q=80" alt="Раковина">
                    <div class="card-info">
                        <strong>Тумба с<br>раковиной</strong>
                        <span>19800 сом</span>
                        <button class="buy-btn" onclick="addToCart('Тумба с раковиной', 19800)">В КОРЗИНУ</button>
                    </div>
                </div>
            </div>

            <!-- Ряд 2, Колонка 1 (Дубль ванной для соответствия макету) -->
            <div class="category-block">
                <div class="category-name">■ Мебель для ванной</div>
                <div class="card-wrapper card-horizontal">
                    <img src="https://images.unsplash.com/photo-1584622650111-993a426fbf0a?auto=format&fit=crop&w=200&q=80" alt="Раковина">
                    <div class="card-info">
                        <strong>Тумба с<br>раковиной</strong>
                        <span>19800 сом</span>
                        <button class="buy-btn" onclick="addToCart('Тумба с раковиной', 19800)">В КОРЗИНУ</button>
                    </div>
                </div>
            </div>

            <!-- Ряд 2, Колонка 2 -->
            <div class="category-block">
                <div class="category-name">■ Мебель для кухни</div>
                <div class="card-wrapper card-horizontal">
                    <img src="https://images.unsplash.com/photo-1577140917170-285929fb55b7?auto=format&fit=crop&w=200&q=80" alt="Стол">
                    <div class="card-info">
                        <strong>Обеденный стол</strong>
                        <span>25000 сом</span>
                        <button class="buy-btn" onclick="addToCart('Обеденный стол', 25000)">В КОРЗИНУ</button>
                    </div>
                </div>
            </div>

            <!-- Ряд 2, Колонка 3 -->
            <div class="category-block">
                <div class="category-name">■ Мебель для детской комнаты</div>
                <div class="card-wrapper card-horizontal">
                    <img src="https://images.unsplash.com/photo-1558603668-6570496b66f8?auto=format&fit=crop&w=200&q=80" alt="Двухъярусная кровать">
                    <div class="card-info">
                        <strong>Двухъярусная<br>кровать</strong>
                        <span>32900 сом</span>
                        <button class="buy-btn" onclick="addToCart('Двухъярусная кровать', 32900)">В КОРЗИНУ</button>
                    </div>
                </div>
            </div>

        </div>
    </main>

    <!-- КОНТАКТЫ (ФУТЕР) -->
    <div class="footer-contacts">
        <div class="footer-contacts-title">contacts-section</div>
        <div class="footer-phone-box">
            tel:... +996 553 548 008
        </div>
    </div>
    
    <div class="copyright">
        Copyright 2000-2026 Pixel Furniture Megamarket<br>
        Built with ❤️ for true retro gamers
    </div>

    <!-- =========================================
         ВСПЛЫВАЮЩИЕ ОКНА (МОДАЛКИ)
    ========================================= -->

    <!-- МОДАЛКА: КОРЗИНА -->
    <div id="cartModal" class="modal">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('cartModal')">&times;</span>
            <h2 class="modal-title">🛒 ИНВЕНТАРЬ</h2>
            
            <ul id="cartItemsList" class="cart-items-list">
                <!-- Товары рендерятся через JS -->
            </ul>
            
            <div class="cart-total">ИТОГО: <span id="cartTotalSum">0</span> сом</div>
            <a id="whatsappCheckoutBtn" href="#" target="_blank" class="whatsapp-btn" style="display: none;">ПОДТВЕРДИТЬ ЗАКАЗ В WA</a>
        </div>
    </div>

    <!-- МОДАЛКА: АКЦИИ -->
    <div id="promoModal" class="modal">
        <div class="modal-content" style="text-align: center;">
            <span class="close-modal" onclick="closeModal('promoModal')">&times;</span>
            <h2 class="modal-title">🎁 СЕКРЕТНЫЙ УРОВЕНЬ</h2>
            <p style="font-size: 1.2rem; margin-bottom: 20px;">Поздравляем! Вы нашли секретную акцию!</p>
            <div style="background: #000; color: #0f0; padding: 20px; font-family: var(--font-pixel); font-size: 2rem; letter-spacing: 5px;">
                PROMO: PIXEL10
            </div>
            <p style="margin-top: 20px;">Назовите этот код при заказе в WhatsApp и получите скидку 10% на весь чек!</p>
        </div>
    </div>

    <!-- МОДАЛКА: КОНТАКТЫ -->
    <div id="contactModal" class="modal">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('contactModal')">&times;</span>
            <h2 class="modal-title">📡 СВЯЗЬ С БАЗОЙ</h2>
            <p><strong>Адрес:</strong> Кыргызстан, г. Бишкек (Пиксельный район, ул. 8-бит, д. 256)</p>
            <br>
            <p><strong>График:</strong> 24/7 (Наши NPC никогда не спят)</p>
            <br>
            <p><strong>Телефон / WhatsApp:</strong> <a href="tel:+996553548008" style="color: var(--accent-orange); font-weight: bold;">+996 553 548 008</a></p>
        </div>
    </div>

    <!-- КОНТЕЙНЕР ДЛЯ ТОСТОВ (УВЕДОМЛЕНИЙ) -->
    <div id="toast-container"></div>

    <!-- =========================================
         JAVASCRIPT ЛОГИКА
    ========================================= -->
    <script>
        // --- 1. ЛОГИКА КОРЗИНЫ С СОХРАНЕНИЕМ (LocalStorage) ---
        let cart = JSON.parse(localStorage.getItem('pixelCart')) || [];

        // Инициализация при загрузке
        document.addEventListener('DOMContentLoaded', () => {
            updateCartCount();
        });

        // Добавление в корзину
        function addToCart(name, price) {
            cart.push({ name: name, price: price, id: Date.now() });
            saveCart();
            updateCartCount();
            showToast(`Товар "${name}" добавлен!`);
            
            // Если корзина открыта - обновляем вид
            if(document.getElementById('cartModal').style.display === 'block') {
                renderCart();
            }
        }

        // Удаление из корзины
        function removeItem(id) {
            cart = cart.filter(item => item.id !== id);
            saveCart();
            updateCartCount();
            renderCart();
        }

        // Сохранение в память браузера
        function saveCart() {
            localStorage.setItem('pixelCart', JSON.stringify(cart));
        }

        // Обновление счетчика на кнопке в шапке
        function updateCartCount() {
            document.getElementById('cart-count').textContent = cart.length;
        }

        // Рендер списка внутри модального окна
        function renderCart() {
            const list = document.getElementById('cartItemsList');
            const btn = document.getElementById('whatsappCheckoutBtn');
            const totalEl = document.getElementById('cartTotalSum');
            
            list.innerHTML = '';
            
            if (cart.length === 0) {
                list.innerHTML = '<li style="text-align:center; padding: 20px; font-style: italic;">Инвентарь пуст. Пора лутаться!</li>';
                btn.style.display = 'none';
                totalEl.textContent = '0';
                return;
            }
            
            btn.style.display = 'block';
            let total = 0;
            let text = 'Привет! Хочу заказать пиксельную мебель:\n\n';

            cart.forEach((item, index) => {
                total += item.price;
                text += `${index + 1}. ${item.name} - ${item.price} сом\n`;
                
                list.innerHTML += `
                    <li class="cart-item">
                        <div class="cart-item-info">
                            <strong>${item.name}</strong>
                            <span class="cart-item-price">${item.price} сом</span>
                        </div>
                        <button class="remove-btn" onclick="removeItem(${item.id})">УДАЛИТЬ</button>
                    </li>
                `;
            });
            
            totalEl.textContent = total;
            text += `\nИтого: ${total} сом`;
            btn.href = 'https://wa.me/996553548008?text=' + encodeURIComponent(text);
        }

        // --- 2. УПРАВЛЕНИЕ МОДАЛЬНЫМИ ОКНАМИ ---
        function openModal(modalId) {
            document.getElementById(modalId).style.display = 'block';
            if(modalId === 'cartModal') renderCart();
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        // Закрытие модалок по клику на темный фон
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        }

        // --- 3. СИСТЕМА УВЕДОМЛЕНИЙ (ТОСТЫ) ---
        function showToast(message) {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.innerHTML = `<span class="toast-icon">✅</span> <span>${message}</span>`;
            
            container.appendChild(toast);

            // Удаляем тост из DOM после завершения анимации
            setTimeout(() => {
                toast.remove();
            }, 3000);
        }
    </script>
</body>
</html>
