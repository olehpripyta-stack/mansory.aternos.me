<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MANSORY DONATE</title>
    <!-- Підключаємо шрифт схожий на той, що на скриншоті -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@400;700&display=swap" rel="stylesheet">
    
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Comfortaa', sans-serif;
        }

        body {
            /* Якісний панорамний фон з Майнкрафту */
            background: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), 
                        url('https://images.unsplash.com/photo-1627856013091-fed6e4e30025?q=80&w=1920') no-repeat center center fixed;
            background-size: cover;
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 40px 20px;
            min-height: 100vh;
        }

        /* Шапка сайту */
        .header {
            text-align: center;
            margin-bottom: 40px;
        }

        .logo-title {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            font-size: 28px;
            font-weight: bold;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .logo-diamond {
            font-size: 32px;
        }

        .subtitle {
            margin-top: 10px;
            font-size: 16px;
            color: #dddddd;
        }

        /* Контейнер для карток */
        .cards-container {
            display: flex;
            flex-direction: column;
            gap: 25px;
            width: 100%;
            max-width: 400px;
        }

        /* Стиль картки донату */
        .card {
            background-color: rgba(28, 28, 28, 0.9);
            border-radius: 18px;
            padding: 30px 20px;
            text-align: center;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .card-title {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 20px;
        }

        .dot {
            width: 18px;
            height: 18px;
            border-radius: 50%;
            display: inline-block;
        }

        .dot.vip { background-color: #76ff03; }
        .dot.premium { background-color: #ffca28; }
        .dot.helper { background-color: #ff3d00; }

        .commands {
            font-style: italic;
            color: #b0bec5;
            font-size: 15px;
            margin-bottom: 12px;
            line-height: 1.5;
        }

        .price {
            font-size: 18px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }

        /* Зелена кнопка купити */
        .btn-buy {
            background-color: #00c853;
            color: white;
            border: none;
            padding: 14px 0;
            width: 100%;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.2s, transform 0.1s;
        }

        .btn-buy:hover {
            background-color: #00e676;
        }

        .btn-buy:active {
            transform: scale(0.98);
        }

        /* Стилі для Модального Вікна (Спливаюче повідомлення) */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.3s ease;
            z-index: 1000;
            padding: 20px;
        }

        .modal-overlay.active {
            opacity: 1;
            pointer-events: auto;
        }

        .modal {
            background: #212121;
            padding: 30px 25px;
            border-radius: 16px;
            text-align: center;
            max-width: 360px;
            width: 100%;
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            border: 1px solid #00c853;
            transform: scale(0.8);
            transition: transform 0.3s ease;
        }

        .modal-overlay.active .modal {
            transform: scale(1);
        }

        .modal h3 {
            margin-bottom: 15px;
            font-size: 20px;
        }

        .modal p {
            color: #cfd8dc;
            font-size: 15px;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        .modal p span {
            color: #00e676;
            font-weight: bold;
        }

        .btn-telegram {
            display: inline-block;
            background-color: #0088cc;
            color: white;
            text-decoration: none;
            padding: 12px 25px;
            border-radius: 8px;
            font-weight: bold;
            font-size: 15px;
            transition: background 0.2s;
            margin-bottom: 15px;
            width: 100%;
        }

        .btn-telegram:hover {
            background-color: #24a1de;
        }

        .btn-close {
            background: transparent;
            color: #90a4ae;
            border: none;
            cursor: pointer;
            font-size: 14px;
            text-decoration: underline;
        }

        .btn-close:hover {
            color: #fff;
        }
    </style>
</head>
<body>

    <!-- Шапка -->
    <div class="header">
        <div class="logo-title">
            <span class="logo-diamond">💎</span> MANSORY DONATE
        </div>
        <div class="subtitle">Купівля донату через Telegram</div>
    </div>

    <!-- Список товарів -->
    <div class="cards-container">
        
        <!-- VIP -->
        <div class="card">
            <div class="card-title">
                <span class="dot vip"></span> VIP
            </div>
            <div class="commands">/fly /hat /feed /workbench</div>
            <div class="price">💰 40 грн</div>
            <button class="btn-buy" onclick="openModal()">Купити</button>
        </div>

        <!-- PREMIUM -->
        <div class="card">
            <div class="card-title">
                <span class="dot premium"></span> PREMIUM
            </div>
            <div class="commands">/heal /enderchest /homes</div>
            <div class="price">💰 60 грн</div>
            <button class="btn-buy" onclick="openModal()">Купити</button>
        </div>

        <!-- HELPER -->
        <div class="card">
            <div class="card-title">
                <span class="dot helper"></span> HELPER
            </div>
            <div class="commands">/kick /mute /tempmute</div>
            <div class="price">💰 100 грн</div>
            <button class="btn-buy" onclick="openModal()">Купити</button>
        </div>

    </div>

    <!-- Модальне вікно при натисканні на Купити -->
    <div class="modal-overlay" id="modalOverlay" onclick="closeModalOutside(event)">
        <div class="modal">
            <h3>Оформлення купівлі</h3>
            <p>Для покупки напишіть у telegram <span>@Lariskcar</span></p>
            <!-- Посилання відразу відкриває чат з користувачем -->
            <a href="https://t.me/Lariskcar" target="_blank" class="btn-telegram">Написати в Telegram</a>
            <br>
            <button class="btn-close" onclick="closeModal()">Закрити</button>
        </div>
    </div>

    <!-- Логіка для відкриття/закриття вікна -->
    <script>
        const modalOverlay = document.getElementById('modalOverlay');

        function openModal() {
            modalOverlay.classList.add('active');
        }

        function closeModal() {
            modalOverlay.classList.remove('active');
        }

        // Закриття вікна, якщо клікнути повз нього
        function closeModalOutside(event) {
            if (event.target === modalOverlay) {
                closeModal();
            }
        }
    </script>

</body>
</html>
