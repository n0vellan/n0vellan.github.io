<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>N0VELLAN Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
    <style>
        /* Estilos base */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', 'Helvetica Neue', Arial, sans-serif;
        }
        
        body {
            background-color: #0c0c0c;
            color: #9a9a9a;
            overflow-x: hidden;
            scroll-behavior: smooth;
            opacity: 0;
            animation: fadeInPage 1.5s ease-out forwards;
        }
        
        @keyframes fadeInPage {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }
        
        .container {
            width: 100%;
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Navegación */
        nav {
            display: flex;
            justify-content: flex-end;
            align-items: center;
            padding: 40px 0;
        }
        
        /* Botón CTA más pequeño */
        .cta-button {
            background: linear-gradient(135deg, #0d2c54, #1e5799);
            border: none;
            color: #fff;
            padding: 8px 18px; /* Reducido desde 10px 25px */
            font-size: 12px; /* Reducido desde 14px */
            letter-spacing: 1px;
            cursor: pointer;
            transition: all 0.3s;
            font-family: 'Montserrat', sans-serif;
            font-weight: 700;
            text-transform: uppercase;
            border-radius: 20px; /* Reducido desde 25px */
            position: relative;
            overflow: hidden;
            box-shadow: 0 4px 12px rgba(13, 44, 84, 0.4);
            display: flex;
            align-items: center;
            gap: 8px; /* Reducido desde 10px */
        }
        
        .cta-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(255,255,255,0.1), rgba(255,255,255,0));
            pointer-events: none;
        }
        
        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(13, 44, 84, 0.6);
            background: linear-gradient(135deg, #1e5799, #0d2c54);
        }
        
        .cta-button:active {
            transform: translateY(1px);
        }
        
        /* Animación del botón cuando se hace clic */
        .button-clicked {
            animation: buttonPulse 0.5s ease-out;
        }
        
        @keyframes buttonPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        .discord-icon {
            width: 16px; /* Reducido desde 18px */
            height: 16px; /* Reducido desde 18px */
            fill: white;
        }
        
        /* Nueva animación para el desplazamiento */
        @keyframes bounceScroll {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-15px); }
            60% { transform: translateY(-7px); }
        }
        
        /* Elemento de indicador de desplazamiento para la animación */
        .scroll-indicator {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 30px;
            height: 50px;
            z-index: 100;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.5s ease;
        }
        
        .scroll-indicator.visible {
            opacity: 1;
            animation: bounceScroll 2s ease infinite;
        }
        
        .scroll-arrow {
            border: solid #fff;
            border-width: 0 3px 3px 0;
            display: inline-block;
            padding: 6px;
            transform: rotate(45deg);
        }
        
        /* Hero section */
        .hero {
            display: grid;
            grid-template-columns: 1fr 1fr;
            min-height: 80vh;
            align-items: center;
            position: relative;
            opacity: 0;
            transform: translateY(30px);
            animation: slideUp 1s ease-out 0.5s forwards;
        }
        
        @keyframes slideUp {
            0% { opacity: 0; transform: translateY(30px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        .hero-text {
            padding-right: 40px;
        }
        
        .name-intro {
            font-size: 1.5rem;
            color: #777;
            margin-bottom: 10px;
            font-weight: 400;
            opacity: 0;
            transform: translateX(-20px);
            animation: slideRight 0.8s ease-out 1s forwards;
        }
        
        @keyframes slideRight {
            0% { opacity: 0; transform: translateX(-20px); }
            100% { opacity: 1; transform: translateX(0); }
        }
        
        .hero-text h1 {
            font-size: 5rem;
            line-height: 1;
            font-weight: 700;
            color: #fff;
            margin-bottom: 30px;
            letter-spacing: -1px;
            opacity: 0;
            transform: translateX(-20px);
            animation: slideRight 0.8s ease-out 1.3s forwards;
        }
        
        .hero-text p {
            color: #777;
            font-size: 1.2rem;
            margin-top: 20px;
            letter-spacing: 1px;
            text-transform: uppercase;
            font-weight: 700;
            opacity: 0;
            transform: translateX(-20px);
            animation: slideRight 0.8s ease-out 1.6s forwards;
        }
        
        .video-preview {
            width: 100%;
            aspect-ratio: 1;
            background: radial-gradient(circle, #1e5799, #0d2c54);
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            opacity: 0;
            transform: translateX(20px);
            animation: slideLeft 0.8s ease-out 1.3s forwards;
            border-radius: 10px;
            box-shadow: 0 15px 30px rgba(0,0,0,0.3);
            overflow: hidden;
        }
        
        @keyframes slideLeft {
            0% { opacity: 0; transform: translateX(20px); }
            100% { opacity: 1; transform: translateX(0); }
        }
        
        .video-preview::after {
            content: "";
            width: 0;
            height: 0;
            border-top: 20px solid transparent;
            border-bottom: 20px solid transparent;
            border-left: 30px solid #fff;
            position: absolute;
            filter: drop-shadow(0 0 5px rgba(0,0,0,0.5));
        }
        
        .video-preview::before {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0) 70%);
            transform: rotate(45deg);
            top: -50%;
            left: -50%;
            transition: all 0.5s;
        }
        
        .video-preview:hover::before {
            left: 100%;
            top: 100%;
        }
        
        /* Nuevo tobogan de tecnologías horizontal */
        .tech-tobogan-section {
            padding: 100px 0;
            position: relative;
            min-height: 400px;
            opacity: 0;
            transform: translateY(30px);
            animation: slideUp 1s ease-out 1.8s forwards;
            overflow: hidden;
        }
        
        .tech-path {
            position: relative;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
        }
        
        /* Contenedor de tecnologías horizontal */
        .tech-bubbles-container {
            width: 100%;
            height: 180px;
            overflow: hidden;
            position: relative;
            margin-bottom: 50px;
        }
        
        .tech-bubbles-track {
            display: flex;
            position: relative;
            animation: scrollBubblesHorizontal 20s linear infinite;
        }
        
        @keyframes scrollBubblesHorizontal {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }
        
        /* Elemento tecnología */
        .tech-bubble-track-item {
            margin: 0 30px;
            transition: all 0.3s;
            opacity: 0.8;
            flex-shrink: 0;
        }
        
        .tech-bubble-track-item:hover {
            opacity: 1;
            transform: translateY(-10px);
        }
        
        /* Elemento tecnología (ahora rectangular y transparente) */
        .tech-bubble {
            width: 140px;
            height: 140px;
            background-color: rgba(13, 44, 84, 0.1);
            border: 2px solid rgba(30, 87, 153, 0.3);
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            box-shadow: 0 5px 15px rgba(13, 44, 84, 0.2);
            backdrop-filter: blur(5px);
            position: relative;
            z-index: 2;
            transition: all 0.3s;
        }
        
        .tech-bubble:hover {
            background-color: rgba(13, 44, 84, 0.3);
            border-color: rgba(30, 87, 153, 0.7);
            transform: scale(1.05);
            box-shadow: 0 8px 25px rgba(13, 44, 84, 0.4);
        }
        
        .tech-bubble img {
            width: 60px;
            height: 60px;
            object-fit: contain;
            margin-bottom: 10px;
        }
        
        .tech-bubble span {
            color: #fff;
            font-weight: 700;
        }
        
        /* Área de discord info */
        .discord-info {
            margin-top: 50px;
            width: 400px;
            background: rgba(13, 44, 84, 0.3);
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            text-align: center;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(30, 87, 153, 0.5);
            position: relative;
            z-index: 5;
        }
        
        .discord-avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            margin: 0 auto 20px;
            border: 3px solid #5865F2;
            box-shadow: 0 5px 15px rgba(88, 101, 242, 0.5);
            background-size: cover;
            background-position: center;
        }
        
        .discord-username {
            color: #fff;
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 5px;
        }
        
        .discord-id {
            color: #aaa;
            font-size: 1rem;
            margin-bottom: 20px;
        }
        
        .discord-button {
            background-color: #5865F2;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }
        
        .discord-button:hover {
            background-color: #4752C4;
            transform: translateY(-2px);
        }
        
        /* Área de texto de experiencia */
        .experience-section {
            padding: 100px 0;
            text-align: center;
            opacity: 0;
            transform: translateY(30px);
            animation: slideUp 1s ease-out 2.1s forwards;
            margin-top: 100px;
        }
        
        .experience-content {
            max-width: 800px;
            margin: 0 auto;
            text-align: left;
        }
        
        .experience-content h2 {
            color: #fff;
            margin-bottom: 30px;
            font-size: 2.5rem;
            text-align: center;
            position: relative;
            display: inline-block;
        }
        
        .experience-content h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, #0d2c54, transparent);
        }
        
        .experience-content p {
            color: #aaa;
            line-height: 1.8;
            margin-bottom: 20px;
            font-size: 1.1rem;
        }
    </style>
</head>
<body>
    <!-- Indicador de desplazamiento para la animación -->
    <div class="scroll-indicator" id="scrollIndicator">
        <div class="scroll-arrow"></div>
    </div>

    <div class="container">
        <nav>
            <button class="cta-button" onclick="scrollToDiscordInfo()">
                <svg class="discord-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 127.14 96.36">
                    <path fill="#fff" d="M107.7,8.07A105.15,105.15,0,0,0,81.47,0a72.06,72.06,0,0,0-3.36,6.83A97.68,97.68,0,0,0,49,6.83,72.37,72.37,0,0,0,45.64,0,105.89,105.89,0,0,0,19.39,8.09C2.79,32.65-1.71,56.6.54,80.21h0A105.73,105.73,0,0,0,32.71,96.36,77.7,77.7,0,0,0,39.6,85.25a68.42,68.42,0,0,1-10.85-5.18c.91-.66,1.8-1.34,2.66-2a75.57,75.57,0,0,0,64.32,0c.87.71,1.76,1.39,2.66,2a68.68,68.68,0,0,1-10.87,5.19,77,77,0,0,0,6.89,11.1A105.25,105.25,0,0,0,126.6,80.22h0C129.24,52.84,122.09,29.11,107.7,8.07ZM42.45,65.69C36.18,65.69,31,60,31,53s5-12.74,11.43-12.74S54,46,53.89,53,48.84,65.69,42.45,65.69Zm42.24,0C78.41,65.69,73.25,60,73.25,53s5-12.74,11.44-12.74S96.23,46,96.12,53,91.08,65.69,84.69,65.69Z"/>
                </svg>
                Discord
            </button>
        </nav>
        
        <section class="hero">
            <div class="hero-text">
                <p class="name-intro">Hi my name is</p>
                <h1>
                    N0VELLAN
                </h1>
                <p>I JUST LIKE PROGRAMMING</p>
            </div>
            
            <div class="video-preview" onclick="scrollToTech()">
            </div>
        </section>
        
        <section id="tech-section" class="tech-tobogan-section">
            <div class="tech-path">
                <!-- Contenedor de tecnologías animado horizontal -->
                <div class="tech-bubbles-container">
                    <div class="tech-bubbles-track" id="techTrack">
                        <!-- Las tecnologías con sus respectivas imágenes -->
                        <div class="tech-bubble-track-item">
                            <div class="tech-bubble">
                                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Lua-Logo.svg/128px-Lua-Logo.svg.png" alt="Lua" />
                                <span>Lua</span>
                            </div>
                        </div>
                        <div class="tech-bubble-track-item">
                            <div class="tech-bubble">
                                <img src="https://imgs.search.brave.com/va692JH018MJaLTBGo1ElcX59bzFmJo7-DsH9B5TlfI/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9jZG4u/d29ybGR2ZWN0b3Js/b2dvLmNvbS9sb2dv/cy9weXRob24tNS5z/dmc" alt="Python" />
                                <span>Python</span>
                            </div>
                        </div>
                        <div class="tech-bubble-track-item">
                            <div class="tech-bubble">
                                <img src="https://imgs.search.brave.com/Fi_FpMp_GH2w9zhhN2YqKjziUcQn2axPqc8UQ7vSKhY/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9icmFu/ZHNsb2dvcy5jb20v/d3AtY29udGVudC91/cGxvYWRzL2ltYWdl/cy9qYXZhLWxvZ28t/MS5wbmc" alt="Java" />
                                <span>Java</span>
                            </div>
                        </div>
                        <div class="tech-bubble-track-item">
                            <div class="tech-bubble">
                                <img src="https://imgs.search.brave.com/8OroAJe18O-R-d4ooE29uoVOKB7xoJwKPIkm3lSu8Cc/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly91cGxv/YWQud2lraW1lZGlh/Lm9yZy93aWtpcGVk/aWEvY29tbW9ucy90/aHVtYi82LzYxL0hU/TUw1X2xvZ29fYW5k/X3dvcmRtYXJrLnN2/Zy8yMjBweC1IVE1M/NV9sb2dvX2FuZF93/b3JkbWFyay5zdmcu/cG5n" alt="HTML" />
                                <span>HTML</span>
                            </div>
                        </div>
                        <div class="tech-bubble-track-item">
                            <div class="tech-bubble">
                                <img src="https://imgs.search.brave.com/u1VbZMOMhUH1p7Jp7njKO5Z06QQA9_3pOOpT9-dEnSs/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly91cGxv/YWQud2lraW1lZGlh/Lm9yZy93aWtpcGVk/aWEvY29tbW9ucy90/aHVtYi9hL2FiL09m/ZmljaWFsX0NTU19M/b2dvLnN2Zy8yMjBw/eC1PZmZpY2lhbF9D/U1NfTG9nby5zdmcu/cG5n" alt="CSS" />
                                <span>CSS 'LEARNING'</span>
                            </div>
                        </div>
                        <div class="tech-bubble-track-item">
                            <div class="tech-bubble">
                                <img src="https://imgs.search.brave.com/Fi_FpMp_GH2w9zhhN2YqKjziUcQn2axPqc8UQ7vSKhY/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9icmFu/ZHNsb2dvcy5jb20v/d3AtY29udGVudC91/cGxvYWRzL2ltYWdl/cy9qYXZhLWxvZ28t/MS5wbmc" alt="Java" alt="JavaScript" />
                                <span>Java</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Información de Discord -->
                <div id="discord-info" class="discord-info">
                    <div class="discord-avatar" id="discord-avatar"></div>
                    <div class="discord-username" id="discord-username">lt8b</div>
                    <div class="discord-id">ID: 1008569474829525022</div>
                    <button class="discord-button" onclick="openDiscordLink()">
                        <svg class="discord-icon" xmlns="https://i.pinimg.com/736x/81/50/d9/8150d92a8fd9653c907511b1171a5c35.jpg" viewBox="0 0 127.14 96.36" width="18" height="18">
                            <path fill="#fff" d="M107.7,8.07A105.15,105.15,0,0,0,81.47,0a72.06,72.06,0,0,0-3.36,6.83A97.68,97.68,0,0,0,49,6.83,72.37,72.37,0,0,0,45.64,0,105.89,105.89,0,0,0,19.39,8.09C2.79,32.65-1.71,56.6.54,80.21h0A105.73,105.73,0,0,0,32.71,96.36,77.7,77.7,0,0,0,39.6,85.25a68.42,68.42,0,0,1-10.85-5.18c.91-.66,1.8-1.34,2.66-2a75.57,75.57,0,0,0,64.32,0c.87.71,1.76,1.39,2.66,2a68.68,68.68,0,0,1-10.87,5.19,77,77,0,0,0,6.89,11.1A105.25,105.25,0,0,0,126.6,80.22h0C129.24,52.84,122.09,29.11,107.7,8.07ZM42.45,65.69C36.18,65.69,31,60,31,53s5-12.74,11.43-12.74S54,46,53.89,53,48.84,65.69,42.45,65.69Zm42.24,0C78.41,65.69,73.25,60,73.25,53s5-12.74,11.44-12.74S96.23,46,96.12,53,91.08,65.69,84.69,65.69Z"/>
                        </svg>
                        Añadir amigo / Add friend
                    </button>
                </div>
            </div>
        </section>
        
        <section id="experience-section" class="experience-section">
            <div class="experience-content">
                <h2>My Experience</h2>
                <p>I am a developer who enjoys programming. My experience includes working with multiple programming languages and frameworks</p>
                <p>In my projects, I prefer to take my time while writing the cleanest and most efficient code possible.</p>
                <p>I decided to create this page for fun and to showcase my passion for programming and software development.</p>
                <p>My goal is to enjoy my favorite hobby. You can contact me on Discord. I can make an HTML page for you as long as it's not too difficult :D.</p>
            </div>
        </section>
    </div>
    
    <script>
        // Función para desplazamiento suave a la información de Discord con animación del botón y flecha
        function scrollToDiscordInfo() {
            const button = document.querySelector('.cta-button');
            const scrollIndicator = document.getElementById('scrollIndicator');
            
            // Animación del botón
            button.classList.add('button-clicked');
            
            // Mostrar el indicador de desplazamiento
            scrollIndicator.classList.add('visible');
            
            // Quitar la clase después de que termine la animación
            setTimeout(function() {
                button.classList.remove('button-clicked');
            }, 500);
            
            // Realizar desplazamiento suave después de un pequeño retraso para mostrar la animación
            setTimeout(function() {
                document.getElementById('discord-info').scrollIntoView({
                    behavior: 'smooth',
                    block: 'center'
                });
                
                // Ocultar el indicador de desplazamiento después del desplazamiento
                setTimeout(function() {
                    scrollIndicator.classList.remove('visible');
                }, 1000);
            }, 800);
        }
        
        // Función para desplazamiento suave a la sección de tecnologías
        function scrollToTech() {
            document.getElementById('tech-section').scrollIntoView({behavior: 'smooth'});
        }
        
        // Función para abrir el enlace de Discord
        function openDiscordLink() {
            window.location.href = "https://discord.com/channels/@me";
        }
        
        // Duplicar las tecnologías para la animación infinita horizontal
        function duplicateTechBubbles() {
            const trackElement = document.getElementById('techTrack');
            const bubbleItems = trackElement.querySelectorAll('.tech-bubble-track-item');
            
            // Clonar cada elemento y añadirlo al track original
            bubbleItems.forEach(item => {
                const clone = item.cloneNode(true);
                trackElement.appendChild(clone);
            });
            
            // Duplicar todo el conjunto una vez más para asegurar desplazamiento continuo
            const allItems = trackElement.querySelectorAll('.tech-bubble-track-item');
            allItems.forEach(item => {
                const clone = item.cloneNode(true);
                trackElement.appendChild(clone);
            });
        }
        
        // Cargar la información de Discord
        function loadDiscordInfo() {
            // URL real que sería: https://i.pinimg.com/736x/81/50/d9/8150d92a8fd9653c907511b1171a5c35.jpg
            document.getElementById('discord-avatar').style.backgroundImage = "url('https://i.pinimg.com/736x/4f/08/b0/4f08b03255307e8a8ecb329c6612a0a1.jpg')";
            document.getElementById('discord-username').textContent = "lt8b";
        }
        
        // Inicializar cuando se cargue la página
        window.addEventListener('load', function() {
            duplicateTechBubbles();
            loadDiscordInfo();
            
            // Pausar la animación cuando se pasa el ratón por encima
            const container = document.querySelector('.tech-bubbles-container');
            const track = document.querySelector('.tech-bubbles-track');
            
            container.addEventListener('mouseenter', function() {
                track.style.animationPlayState = 'paused';
            });
            
            container.addEventListener('mouseleave', function() {
                track.style.animationPlayState = 'running';
            });
        });
    </script>
</body>
</html>
