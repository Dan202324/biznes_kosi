<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kosi - Сувениры и корпоративные подарки</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        :root {
            --primary: #6a5acd;
            --secondary: #ff6b6b;
            --accent: #4ecdc4;
            --dark: #2c3e50;
            --light: #f8f9fa;
        }

        body {
            background-color: var(--light);
            color: var(--dark);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--primary);
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            padding: 150px 0 100px;
            text-align: center;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto 2rem;
        }

        .btn {
            display: inline-block;
            background: var(--secondary);
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        /* Products Section */
        .products {
            padding: 80px 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
        }

        .section-title h2 {
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }

        .product-card:hover {
            transform: translateY(-10px);
        }

        .product-img {
            height: 200px;
            background: var(--light);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-info h3 {
            margin-bottom: 1rem;
            color: var(--primary);
        }

        /* About Section */
        .about {
            background: var(--dark);
            color: white;
            padding: 80px 0;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }

        /* Contact Section */
        .contact {
            padding: 80px 0;
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            border-color: var(--primary);
            outline: none;
        }

        .form-group textarea {
            height: 150px;
            resize: vertical;
        }

        /* Notification */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 5px;
            color: white;
            font-weight: bold;
            z-index: 1001;
            transform: translateX(400px);
            transition: transform 0.3s ease;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.success {
            background: #4CAF50;
        }

        .notification.error {
            background: #f44336;
        }

        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            text-align: center;
            padding: 2rem 0;
        }

        /* Loading */
        .loading {
            display: none;
            text-align: center;
            padding: 10px;
        }

        .loading.spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 2s linear infinite;
            margin: 0 auto;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Telegram Widget */
        .telegram-widget {
            background: #0088cc;
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin-top: 20px;
            text-align: center;
        }

        .telegram-widget a {
            color: white;
            text-decoration: none;
            font-weight: bold;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero h1 {
                font-size: 2rem;
            }

            .about-content {
                grid-template-columns: 1fr;
            }
        }
        .wes {
            height: 200px;
        }
        .sew {
            height: 200px;
        }
        .ews {
            height: 200px;
        }
        .esw {
            height: 200px;
        }
        .qwerty {
            height: 200px;
        }
        .product-price {
        font-size: 1.3rem;
        font-weight: bold;
        color: var(--secondary);
        }

        .product-badge {
        position: absolute;
        top: 15px;
        right: 15px;
        background: var(--accent);
        color: white;
        padding: 5px 12px;
        border-radius: 20px;
        font-size: 0.8rem;
        font-weight: bold;
        }
    </style>
</head>
<body>
    <!-- Notification -->
    <div id="notification" class="notification"></div>

    <!-- Header -->
    <header>
        <div class="container">
            <nav>
                <div class="logo">Kosi</div>
                <div class="nav-links">
                    <a href="#products">Продукты</a>
                    <a href="#about">О нас</a>
                    <a href="#contact">Заказать</a>
                </div>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h1>Создаём эмоции в деталях</h1>
            <p>Магниты, 3D стикеры, шоколад с логотипом, именные ручки, альбомы-брелки — всё для ваших особенных моментов</p>
            <a href="#contact" class="btn">Сделать заказ</a>
        </div>
    </section>

    <!-- Products Section -->
    <section id="products" class="products">
        <div class="container">
            <div class="section-title">
                <h2>Наша продукция</h2>
                <p>Широкий выбор персонализированных сувениров</p>
            </div>
            <div class="products-grid">
                <div class="product-card">
                    <div class="product-img"><img src="https://psv4.userapi.com/s/v1/d/1xtpd2Y6_NaycJNiwsKIImU7v2Xz5C13hRppONskiCWxTmLGGLEz_UOOQMPsTPlWuoQmytK7dVY4B-8zbaE4csZIb0xk7_q0iSd1CZ2ZogJHKoeoT3OAaA/foto_dlya_zapisi_4.jpg" alt="" class="wes"></div>
                    <div class="product-badge">Хит</div>
                    <div class="product-info">
                        <h3>Авторские магниты</h3>
                        <p>Яркие магнитные сувениры любого размера и формы. Идеально для промо-акций и памятных подарков.</p>
                        <div class="product-price">от 80 ₽/шт</div>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-img"><img src="стикер.jpg" alt="" class="sew"></div>
                    <div class="product-badge">Популярно</div>
                    <div class="product-info">
                        <h3>3D Стикеры</h3>
                        <p>Объёмные наклейки премиум-качества. Превращают обычные вещи в уникальные аксессуары.</p>
                        <div class="product-price">от 65 ₽/шт</div>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-img"><img src="Шоколад1.jpg" alt="" class="ews"></div>
                    <div class="product-info">
                        <h3>Шоколад с логотипом</h3>
                        <p>Вкусный способ сказать "спасибо" клиентам и партнёрам. Качественный шоколад с вашим дизайном.</p>
                        <div class="product-price">от 20 ₽/шт</div>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-img"><img src="Ручки.jpg" alt="" class="qwerty"></div>
                    <div class="product-info">
                        <h3>Именные ручки</h3>
                        <p>Элегантные пишущие инструменты с гравировкой. Корпоративные подарки высшего класса.</p>
                        <div class="product-price">от 70 ₽/шт</div>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-img"><img src="Брелок.jpg" alt="" class="esw"></div>
                    <div class="product-badge">Новинка</div>
                    <div class="product-info">
                        <h3>Альбом-брелок</h3>
                        <p>Стильные фотоальбомы-брелки с индивидуальным дизайном. Для самых ценных воспоминаний.</p>
                        <div class="product-price">от 290 ₽/шт</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
        <div class="container">
            <div class="about-content">
                <div>
                    <h2>Почему выбирают нас?</h2>
                    <p>Мы превращаем обычные вещи в особенные воспоминания. Каждый наш продукт — это не просто сувенир, а эмоция, застывшая в деталях.</p>
                    <br>
                    <p>Работаем как с корпоративными клиентами, так и с частными лицами. Создаём уникальные решения для ваших событий, промо-акций и бизнес-задач.</p>
                </div>
                <div>
                    <h3>Наши преимущества</h3>
                    <ul style="list-style-position: inside; line-height: 2;">
                        <li>Индивидуальный подход к каждому заказу</li>
                        <li>Современное оборудование и материалы</li>
                        <li>Строгий контроль качества</li>
                        <li>Соблюдение сроков</li>
                        <li>Помощь в разработке дизайна</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
        <div class="container">
            <div class="section-title">
                <h2>Сделать заказ</h2>
                <p>Расскажите нам о вашем проекте, и мы предложим лучшее решение</p>
            </div>
            <div class="contact-form">
                <form id="orderForm">
                    <div class="form-group">
                        <label for="name">Ваше имя *</label>
                        <input type="text" id="name" required placeholder="Иван Иванов">
                    </div>
                    <div class="form-group">
                        <label for="phone">Телефон *</label>
                        <input type="tel" id="phone" required placeholder="+7 (999) 123-45-67">
                    </div>
                    <div class="form-group">
                        <label for="product">Интересующий продукт *</label>
                        <select id="product" required>
                            <option value="">Выберите продукт</option>
                            <option value="Магниты">Магниты</option>
                            <option value="3D Стикеры">3D Стикеры</option>
                            <option value="Шоколад с логотипом">Шоколад с логотипом</option>
                            <option value="Именные ручки">Именные ручки</option>
                            <option value="Альбомы">Альбомы-брелок</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="quantity">Примерное количество</label>
                        <input type="text" id="quantity" placeholder="Например: 50 шт, 100 шт...">
                    </div>
                    <div class="form-group">
                        <label for="budget">Бюджет</label>
                        <input type="text" id="budget" placeholder="Примерный бюджет на заказ">
                    </div>
                    <div class="form-group">
                        <label for="message">Детали заказа</label>
                        <textarea id="message" placeholder="Опишите ваш заказ, сроки, особые пожелания, идеи для дизайна..."></textarea>
                    </div>
                    <div class="loading" id="loading">
                        <div class="spinner"></div>
                        <p>Отправляем заявку в Telegram...</p>
                    </div>
                    <button type="submit" class="btn" id="submitBtn">Отправить заявку в Telegram</button>
                </form>
                
                <div class="telegram-widget">
                    <p>💬 Или напишите нам напрямую в Telegram: 
                    <a href="https://t.me/Daniilwes" target="_blank">@Daniilwes</a></p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>© 2023 Kosi. Сувениры и корпоративные подарки</p>
            <p>Связь через Telegram: <a href="https://t.me/Daniilwes" style="color: #4ecdc4;">@Daniilwes</a></p>
            <p>Заявки приходят напрямую в Telegram</p>
        </div>
    </footer>

    <script>
        // Telegram Bot Configuration - ВАШИ ДАННЫЕ
        const TELEGRAM_BOT_TOKEN = '7636180288:AAFV18mFCIs74CZWngBXwZy3Scswpdsdupk';
        const TELEGRAM_CHAT_ID = '@Daniilwes'; // Ваш Telegram username

        // Smooth scroll for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Notification system
        function showNotification(message, type = 'success') {
            const notification = document.getElementById('notification');
            notification.textContent = message;
            notification.className = `notification ${type} show`;
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 5000);
        }

        // Form submission to Telegram
        document.getElementById('orderForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const submitBtn = document.getElementById('submitBtn');
            const loading = document.getElementById('loading');
            
            // Get form data
            const formData = {
                name: document.getElementById('name').value.trim(),
                phone: document.getElementById('phone').value.trim(),
                product: document.getElementById('product').value,
                quantity: document.getElementById('quantity').value.trim(),
                budget: document.getElementById('budget').value.trim(),
                message: document.getElementById('message').value.trim(),
                date: new Date().toLocaleString('ru-RU'),
                source: 'Сайт Memoria'
            };

            // Basic validation
            if (!formData.name || !formData.phone || !formData.product) {
                showNotification('❌ Пожалуйста, заполните обязательные поля', 'error');
                return;
            }

            // Show loading
            submitBtn.disabled = true;
            loading.style.display = 'block';

            // Create message text for Telegram
            const telegramMessage = `
🎉 *НОВАЯ ЗАЯВКА С САЙТА* 🎉

👤 *Имя:* ${formData.name}
📞 *Телефон:* ${formData.phone}
📦 *Продукт:* ${formData.product}
📊 *Количество:* ${formData.quantity || 'Не указано'}
💰 *Бюджет:* ${formData.budget || 'Не указан'}
📝 *Детали:* ${formData.message || 'Не указаны'}
⏰ *Дата:* ${formData.date}
🌐 *Источник:* ${formData.source}

🚀 *Срочно свяжись с клиентом!*
            `.trim();

            try {
                // Send to Telegram using Bot API
                const response = await fetch(`https://api.telegram.org/bot${TELEGRAM_BOT_TOKEN}/sendMessage`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        chat_id: TELEGRAM_CHAT_ID,
                        text: telegramMessage,
                        parse_mode: 'Markdown'
                    })
                });

                const result = await response.json();

                if (result.ok) {
                    showNotification('✅ Заявка успешно отправлена! Мы свяжемся с вами в Telegram в ближайшее время.', 'success');
                    // Reset form
                    this.reset();
                } else {
                    throw new Error(result.description || 'Telegram API error');
                }

            } catch (error) {
                console.error('Error sending to Telegram:', error);
                showNotification('❌ Ошибка отправки. Пожалуйста, свяжитесь с нами напрямую через Telegram: @Daniilwes', 'error');
            } finally {
                // Hide loading
                submitBtn.disabled = false;
                loading.style.display = 'none';
            }
        });

        // Phone number formatting
        document.getElementById('phone').addEventListener('input', function(e) {
            let value = e.target.value.replace(/\D/g, '');
            
            // Format Russian phone number
            if (value.length === 0) return;
            
            let formattedValue = '+7 ';
            
            if (value.length > 1) {
                value = value.substring(1); // Remove leading 7 or 8
            }
            
            if (value.length > 0) {
                formattedValue += '(' + value.substring(0, 3);
            }
            if (value.length > 3) {
                formattedValue += ') ' + value.substring(3, 6);
            }
            if (value.length > 6) {
                formattedValue += '-' + value.substring(6, 8);
            }
            if (value.length > 8) {
                formattedValue += '-' + value.substring(8, 10);
            }
            
            e.target.value = formattedValue;
        });

        // Add some interactive effects
        document.addEventListener('DOMContentLoaded', function() {
            // Animate product cards on scroll
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            };

            const observer = new IntersectionObserver(function(entries) {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, observerOptions);

            // Observe product cards
            document.querySelectorAll('.product-card').forEach(card => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(20px)';
                card.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
                observer.observe(card);
            });
        });
    </script>
</body>
</html>

