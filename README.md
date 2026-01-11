[DVesti-Shop.html](https://github.com/user-attachments/files/24547898/DVesti-Shop.html)
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Стилист - Умный подбор одежды из официальных магазинов</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* === БАЗОВЫЕ СТИЛИ === */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
            color: #333;
            line-height: 1.6;
            background-color: #fff;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        section {
            padding: 80px 0;
        }

        /* === НОВАЯ ЦВЕТОВАЯ ПАЛИТРА: САЛАТОВО-БЕЖЕВЫЕ ТОНА === */
        :root {
            --primary: #9ACD32;      /* Салатовый */
            --primary-dark: #7CB342; /* Темно-салатовый */
            --secondary: #F5E6D3;    /* Бежевый фон */
            --accent: #D4A574;       /* Бежевый акцент */
            --light: #FAF3E6;        /* Светло-бежевый */
            --dark: #5D4037;         /* Темный для текста */
            --gray: #8D6E63;         /* Серо-бежевый */
        }

        /* === ТИПОГРАФИЯ И КНОПКИ === */
        h1 {
            font-size: 3.5rem;
            font-weight: 800;
            line-height: 1.2;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            text-align: center;
            color: var(--dark);
        }

        h3 {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 1rem;
            color: var(--dark);
        }

        .gradient-text {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 15px 35px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(154, 205, 50, 0.2);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(154, 205, 50, 0.3);
        }

        .btn-outline {
            background: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }

        .btn-outline:hover {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
        }

        /* === ШАПКА === */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 20px 0;
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.05);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 800;
            color: var(--dark);
            text-decoration: none;
        }

        .logo span {
            color: var(--primary);
        }

        nav {
            display: flex;
            gap: 40px;
        }

        nav a {
            color: var(--gray);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        nav a:hover {
            color: var(--primary);
        }

        /* === ПОИСКОВАЯ ФОРМА В ШАПКЕ === */
        .search-form {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .search-input {
            padding: 10px 20px;
            border: 2px solid var(--light);
            border-radius: 50px;
            font-size: 1rem;
            width: 300px;
            transition: all 0.3s;
            background: var(--light);
        }

        .search-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(154, 205, 50, 0.1);
        }

        .search-btn {
            background: var(--primary);
            color: white;
            border: none;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .search-btn:hover {
            background: var(--primary-dark);
            transform: scale(1.05);
        }

        /* === ГЛАВНЫЙ БАННЕР === */
        .hero {
            padding-top: 160px;
            padding-bottom: 100px;
            background: linear-gradient(135deg, var(--light) 0%, var(--secondary) 100%);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -20%;
            width: 600px;
            height: 600px;
            background: linear-gradient(135deg, rgba(154, 205, 50, 0.1) 0%, rgba(123, 179, 66, 0.1) 100%);
            border-radius: 50%;
        }

        .hero p {
            font-size: 1.2rem;
            color: var(--gray);
            max-width: 800px;
            margin: 0 auto 40px;
        }

        .search-example {
            display: inline-block;
            background: white;
            padding: 20px 30px;
            border-radius: 15px;
            margin-top: 40px;
            font-style: italic;
            color: var(--gray);
            border-left: 4px solid var(--primary);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
        }

        /* === ФУНКЦИИ ПОИСКА === */
        .features {
            background: white;
        }

        .section-subtitle {
            text-align: center;
            color: var(--gray);
            max-width: 600px;
            margin: 0 auto 60px;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
            margin-top: 60px;
        }

        .feature-card {
            background: var(--light);
            padding: 40px 30px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease;
            border: 1px solid var(--secondary);
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 50px rgba(154, 205, 50, 0.1);
        }

        .feature-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 25px;
            color: white;
            font-size: 2rem;
        }

        .params-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-top: 20px;
        }

        .param {
            background: rgba(154, 205, 50, 0.1);
            padding: 10px;
            border-radius: 10px;
            font-size: 0.9rem;
            color: var(--primary-dark);
            font-weight: 500;
        }

        /* === ТЕХНОЛОГИЯ === */
        .technology {
            background: var(--secondary);
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 30px;
            margin-top: 60px;
        }

        .tech-card {
            background: white;
            padding: 40px 25px;
            border-radius: 20px;
            text-align: center;
            position: relative;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.05);
            border: 1px solid var(--light);
        }

        .tech-number {
            font-size: 5rem;
            font-weight: 800;
            color: rgba(245, 230, 211, 0.5);
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1;
        }

        .tech-content {
            position: relative;
            z-index: 2;
        }

        .tech-icon {
            width: 60px;
            height: 60px;
            background: rgba(154, 205, 50, 0.1);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            color: var(--primary);
            font-size: 1.5rem;
        }

        /* === СТИЛИ ОБРАЗОВ === */
        .style-section {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            text-align: center;
        }

        .style-section h2 {
            color: white;
        }

        .style-tags {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 40px 0;
            flex-wrap: wrap;
        }

        .style-tag {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            padding: 12px 30px;
            border-radius: 50px;
            font-weight: 600;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .style-features {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-top: 60px;
        }

        .style-feature {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(10px);
            padding: 30px 20px;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.25);
        }

        .style-feature h4 {
            color: white;
            margin-bottom: 10px;
        }

        /* === ОТЗЫВЫ === */
        .reviews {
            background: var(--light);
        }

        .reviews-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
            margin-top: 60px;
        }

        .review-card {
            background: white;
            padding: 40px 30px;
            border-radius: 20px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.05);
            border: 1px solid var(--secondary);
            transition: transform 0.3s ease;
        }

        .review-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 50px rgba(154, 205, 50, 0.1);
        }

        .review-header {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
        }

        .review-avatar {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 20px;
            color: white;
            font-weight: bold;
            font-size: 1.5rem;
        }

        .review-info h4 {
            margin-bottom: 5px;
            color: var(--dark);
        }

        .review-info p {
            color: var(--gray);
            font-size: 0.9rem;
        }

        .review-rating {
            color: #FFC107;
            margin: 15px 0;
            font-size: 1.1rem;
        }

        /* === ПОДВАЛ === */
        footer {
            background: var(--dark);
            color: #BDBDBD;
            padding: 80px 0 40px;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            flex-wrap: wrap;
            gap: 40px;
        }

        .footer-logo {
            font-size: 1.8rem;
            font-weight: 800;
            color: white;
            margin-bottom: 20px;
            display: block;
        }

        .footer-logo span {
            color: var(--primary);
        }

        .footer-links {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .footer-links a {
            color: #BDBDBD;
            text-decoration: none;
            transition: color 0.3s;
        }

        .footer-links a:hover {
            color: var(--primary);
        }

        .copyright {
            text-align: center;
            margin-top: 60px;
            padding-top: 30px;
            border-top: 1px solid #4E342E;
            color: #8D6E63;
            font-size: 0.9rem;
        }

        /* === АДАПТИВНОСТЬ === */
        @media (max-width: 1100px) {
            .header-content {
                flex-direction: column;
                gap: 20px;
            }
            
            nav {
                order: 3;
                margin-top: 20px;
            }
            
            .search-form {
                order: 2;
            }
        }

        @media (max-width: 1024px) {
            .features-grid,
            .tech-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .reviews-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .style-features {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            
            h2 {
                font-size: 2rem;
            }
            
            .features-grid,
            .tech-grid,
            .style-features,
            .reviews-grid {
                grid-template-columns: 1fr;
            }
            
            .search-input {
                width: 250px;
            }
            
            nav {
                gap: 20px;
                flex-wrap: wrap;
                justify-content: center;
            }
        }

        @media (max-width: 480px) {
            .search-input {
                width: 200px;
            }
            
            .hero {
                padding-top: 200px;
            }
        }
    </style>
</head>
<body>
    <!-- ШАПКА С ПОИСКОВОЙ СТРОКОЙ -->
    <header>
        <div class="container header-content">
            <a href="#" class="logo">D<span>Vesti</span></a>
            
            <!-- ПОИСКОВАЯ ФОРМА -->
            <form class="search-form" id="searchForm">
                <input type="text" class="search-input" placeholder="Ищите одежду, бренды, стили..." id="searchInput">
                <button type="submit" class="search-btn">
                    <i class="fas fa-search"></i>
                </button>
            </form>
            
            <nav>
                <a href="#features">Умный поиск</a>
                <a href="#technology">Технология</a>
                <a href="#style">Подбор образа</a>
                <a href="#reviews">Отзывы</a>
            </nav>
        </div>
    </header>

    <!-- ГЛАВНЫЙ БАННЕР -->
    <section class="hero">
        <div class="container">
            <h1>AI-стилист</h1>
            <p>Умный помощник для подбора одежды из официальных магазинов. Находим идеальные варианты по вашим параметрам: стиль, размер, бренд, цена и многое другое.</p>
            <a href="#features" class="btn">Начать поиск</a>
            <div class="search-example">
                <i class="fas fa-search"></i> Пример запроса: "Ищу минималистичное черное пальто из шерсти, размер M, бюджет до 15000₽, стиль casual-elegant"
            </div>
        </div>
    </section>

    <!-- ФУНКЦИИ ПОИСКА -->
    <section class="features" id="features">
        <div class="container">
            <h2>Найдите идеальную одежду</h2>
            <p class="section-subtitle">Сделайте запрос по интересующим вас параметрам вещи</p>
            
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon"><i class="fas fa-palette"></i></div>
                    <h3>Поиск по стилю</h3>
                    <p>Минималистичный, casual, деловой, спортивный</p>
                    <div class="params-grid">
                        <div class="param">Стиль</div>
                        <div class="param">Крой</div>
                        <div class="param">Силуэт</div>
                    </div>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon"><i class="fas fa-sliders-h"></i></div>
                    <h3>Поиск по параметрам</h3>
                    <p>Размер, цвет, материал, бренд, цена</p>
                    <div class="params-grid">
                        <div class="param">Размер</div>
                        <div class="param">Цвет</div>
                        <div class="param">Материал</div>
                        <div class="param">Бренд</div>
                    </div>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon"><i class="fas fa-wallet"></i></div>
                    <h3>Поиск по бюджету</h3>
                    <p>Укажите желаемый ценовой диапазон</p>
                    <div class="params-grid">
                        <div class="param">Цена от</div>
                        <div class="param">Цена до</div>
                        <div class="param">Скидки</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ТЕХНОЛОГИЯ -->
    <section class="technology" id="technology">
        <div class="container">
            <h2>Умный поиск<br><span class="gradient-text">по параметрам</span></h2>
            
            <div class="tech-grid">
                <div class="tech-card">
                    <div class="tech-number">1</div>
                    <div class="tech-content">
                        <div class="tech-icon"><i class="fas fa-comment-alt"></i></div>
                        <h3>Анализ запроса</h3>
                        <p>AI анализирует ваш текстовый запрос и определяет все важные параметры</p>
                        <div class="params-grid" style="grid-template-columns: repeat(4, 1fr); margin-top: 20px;">
                            <div class="param">Стиль</div>
                            <div class="param">Размер</div>
                            <div class="param">Цвет</div>
                            <div class="param">Бюджет</div>
                        </div>
                    </div>
                </div>
                
                <div class="tech-card">
                    <div class="tech-number">2</div>
                    <div class="tech-content">
                        <div class="tech-icon"><i class="fas fa-store"></i></div>
                        <h3>Поиск в каталогах</h3>
                        <p>Система ищет подходящие варианты в официальных магазинах</p>
                        <div class="params-grid" style="grid-template-columns: repeat(3, 1fr); margin-top: 20px;">
                            <div class="param">Бренды</div>
                            <div class="param">Магазины</div>
                            <div class="param">Наличие</div>
                        </div>
                    </div>
                </div>
                
                <div class="tech-card">
                    <div class="tech-number">3</div>
                    <div class="tech-content">
                        <div class="tech-icon"><i class="fas fa-filter"></i></div>
                        <h3>Умная фильтрация</h3>
                        <p>Фильтруем результаты по множеству параметров для точного соответствия</p>
                        <div class="params-grid" style="grid-template-columns: repeat(4, 1fr); margin-top: 20px;">
                            <div class="param">Материал</div>
                            <div class="param">Качество</div>
                            <div class="param">Принт</div>
                            <div class="param">Крой</div>
                        </div>
                    </div>
                </div>
                
                <div class="tech-card">
                    <div class="tech-number">4</div>
                    <div class="tech-content">
                        <div class="tech-icon"><i class="fas fa-trophy"></i></div>
                        <h3>Лучшие результаты</h3>
                        <p>Получаете подборку идеально подходящих вариантов одежды</p>
                        <div class="params-grid" style="grid-template-columns: repeat(4, 1fr); margin-top: 20px;">
                            <div class="param">Рейтинг</div>
                            <div class="param">Отзывы</div>
                            <div class="param">Фото</div>
                            <div class="param">Ссылки</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- СТИЛИ ОБРАЗОВ -->
    <section class="style-section" id="style">
        <div class="container">
            <h2>Подбор образа<br>в вашем стиле</h2>
            <p style="max-width: 700px; margin: 20px auto 0; color: rgba(255, 255, 255, 0.9);">
                Укажите название стиля в текстовом запросе, и наш AI-помощник подберет полный образ с учетом всех ваших параметров: размера, бренда, принта, кроя, материала, цветовой палитры и бюджета.
            </p>
            
            <div class="style-tags">
                <div class="style-tag">Минимализм</div>
                <div class="style-tag">Casual</div>
                <div class="style-tag">Elegant</div>
            </div>
            
            <a href="#features" class="btn btn-outline">Попробовать подбор</a>
            
            <div class="style-features">
                <div class="style-feature">
                    <h4>Подбор образа по названию стиля</h4>
                    <p>Укажите стиль в запросе</p>
                </div>
                <div class="style-feature">
                    <h4>Учет контекста и предпочтений</h4>
                    <p>Анализ всех предпочтений</p>
                </div>
                <div class="style-feature">
                    <h4>Комплексный анализ всех параметров</h4>
                    <p>Все параметры учтены</p>
                </div>
                <div class="style-feature">
                    <h4>Рекомендации от AI-стилиста</h4>
                    <p>Профессиональный подбор</p>
                </div>
            </div>
        </div>
    </section>

    <!-- ОТЗЫВЫ (ОБНОВЛЕННЫЕ В СООТВЕТСТВИИ С ОРИГИНАЛОМ) -->
    <section class="reviews" id="reviews">
        <div class="container">
            <h2>Отзывы пользователей сервиса <span class="gradient-text">DVesti</span></h2>
            <p class="section-subtitle">Более 10,000 довольных пользователей уже нашли свой идеальный стиль</p>
            
            <div class="reviews-grid">
                <!-- Отзыв 1 -->
                <div class="review-card">
                    <div class="review-header">
                        <div class="review-avatar">АП</div>
                        <div class="review-info">
                            <h4>Анна Петрова</h4>
                            <p>Дизайнер</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p><em>"Невероятно удобно! Раньше тратила часы на поиск подходящей одежды в разных магазинах. Теперь просто описываю, что нужно, и получаю идеальные варианты за минуты."</em></p>
                </div>
                
                <!-- Отзыв 2 -->
                <div class="review-card">
                    <div class="review-header">
                        <div class="review-avatar">ДС</div>
                        <div class="review-info">
                            <h4>Дмитрий Соколов</h4>
                            <p>Менеджер</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p><em>"Отличный AI-помощник! Система действительно понимает запросы и учитывает все параметры. Подобрал костюм для важной встречи - все было идеально по стилю и размеру."</em></p>
                </div>
                
                <!-- Отзыв 3 -->
                <div class="review-card">
                    <div class="review-header">
                        <div class="review-avatar">ЕВ</div>
                        <div class="review-info">
                            <h4>Елена Волкова</h4>
                            <p>Предприниматель</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p><em>"Экономит время и деньги! Больше не покупаю лишнего. AI-стилист помогает найти именно то, что нужно, в рамках бюджета. Очень довольна результатами!"</em></p>
                </div>
                
                <!-- Отзыв 4 -->
                <div class="review-card">
                    <div class="review-header">
                        <div class="review-avatar">АМ</div>
                        <div class="review-info">
                            <h4>Алексей Морозов</h4>
                            <p>Фотограф</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p><em>"Находит редкие вещи! Искал определенный стиль куртки - система нашла варианты, о которых я даже не знал. Отличная подборка из разных магазинов."</em></p>
                </div>
                
                <!-- Отзыв 5 -->
                <div class="review-card">
                    <div class="review-header">
                        <div class="review-avatar">МН</div>
                        <div class="review-info">
                            <h4>Мария Новикова</h4>
                            <p>Стилист</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p><em>"Учитывает все детали! Впечатлена тем, как точно система подбирает одежду по материалам, цветам и стилю. Каждая рекомендация - в точку!"</em></p>
                </div>
                
                <!-- Отзыв 6 -->
                <div class="review-card">
                    <div class="review-header">
                        <div class="review-avatar">ИЛ</div>
                        <div class="review-info">
                            <h4>Игорь Лебедев</h4>
                            <p>Архитектор</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p><em>"Лучший помощник! Использую постоянно для подбора гардероба. Удобный интерфейс, быстрый поиск, отличные результаты. Рекомендую всем!"</em></p>
                </div>
            </div>
        </div>
    </section>

    <!-- ПОДВАЛ -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div>
                    <a href="#" class="footer-logo">D<span>Vesti</span></a>
                    <p style="max-width: 300px; margin-top: 20px; color: #BDBDBD;">AI Стилист - Умный подбор одежды из официальных магазинов</p>
                </div>
                
                <div class="footer-links">
                    <a href="#">Главная</a>
                    <a href="#features">Умный поиск</a>
                    <a href="#technology">Технология</a>
                    <a href="#style">Подбор образа</a>
                    <a href="#reviews">Отзывы</a>
                </div>
            </div>
            
            <div class="copyright">
                <p>© 2024 DVesti AI Стилист. Все права защищены.</p>
            </div>
        </div>
    </footer>

    <script>
        // === ОБРАБОТКА ПОИСКОВОЙ ФОРМЫ ===
        document.getElementById('searchForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const searchQuery = document.getElementById('searchInput').value.trim();
            
            if (searchQuery) {
                alert(`AI-стилист начинает поиск по запросу: "${searchQuery}"\n\nВ реальном приложении здесь будет:\n1. Анализ запроса с помощью NLP\n2. Поиск по каталогам магазинов\n3. Фильтрация результатов\n4. Показ найденных товаров`);
                
                // Здесь в реальном приложении будет AJAX запрос к серверу
                // Например: fetch('/api/search', { method: 'POST', body: JSON.stringify({query: searchQuery}) })
                
                // Очищаем поле поиска
                document.getElementById('searchInput').value = '';
            } else {
                alert('Пожалуйста, введите запрос для поиска');
            }
        });

        // Автозаполнение примерами запросов при фокусе
        document.getElementById('searchInput').addEventListener('focus', function() {
            const examples = [
                "Минималистичное черное пальто",
                "Джинсы casual стиль",
                "Кроссовки Nike размер 42",
                "Костюм для офиса",
                "Летнее платье до 5000₽"
            ];
            
            // Показываем подсказку
            this.setAttribute('placeholder', examples[Math.floor(Math.random() * examples.length)]);
        });
        
        document.getElementById('searchInput').addEventListener('blur', function() {
            this.setAttribute('placeholder', 'Ищите одежду, бренды, стили...');
        });

        // === ПЛАВНАЯ ПРОКРУТКА ===
        document.querySelectorAll('nav a, .footer-links a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                const targetId = this.getAttribute('href');
                if(targetId.startsWith('#')) {
                    e.preventDefault();
                    const targetElement = document.querySelector(targetId);
                    if(targetElement) {
                        window.scrollTo({
                            top: targetElement.offsetTop - 80,
                            behavior: 'smooth'
                        });
                    }
                }
            });
        });

        // === АНИМАЦИЯ ПРИ ПРОКРУТКЕ ===
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
