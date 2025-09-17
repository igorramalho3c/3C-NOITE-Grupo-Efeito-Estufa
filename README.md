<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Efeito Estufa Interativo</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f8ff;
            scroll-behavior: smooth;
        }

        header {
            background: linear-gradient(to right, #4CAF50, #2E8B57);
            color: white;
            text-align: center;
            padding: 30px 20px;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        header h1 {
            margin: 0;
            font-size: 2.5rem;
            animation: fadeInDown 1s ease;
        }

        nav {
            display: flex;
            justify-content: center;
            background-color: #333;
        }

        nav a {
            color: white;
            padding: 14px 20px;
            text-decoration: none;
            text-transform: uppercase;
            font-weight: bold;
            transition: 0.3s;
        }

        nav a:hover {
            background-color: #ddd;
            color: black;
        }

        section {
            max-width: 1000px;
            margin: 40px auto;
            padding: 20px;
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease-out;
        }

        section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        section h2 {
            color: #333;
            margin-bottom: 15px;
            text-align: center;
        }

        section p, section ul {
            margin-bottom: 15px;
        }

        img {
            max-width: 100%;
            border-radius: 10px;
            transition: transform 0.3s;
        }

        img:hover {
            transform: scale(1.05);
        }

        .chart-container {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
        }

        .bar {
            width: 120px;
            margin: 10px;
            text-align: center;
        }

        .bar div {
            background-color: #4CAF50;
            width: 100%;
            height: 0;
            border-radius: 8px;
            transition: height 1.5s ease;
        }

        .bar span {
            display: block;
            margin-top: 8px;
            font-weight: bold;
        }

        footer {
            text-align: center;
            padding: 15px;
            background-color: #333;
            color: white;
            margin-top: 30px;
        }

        @keyframes fadeInDown {
            from {opacity: 0; transform: translateY(-20px);}
            to {opacity: 1; transform: translateY(0);}
        }
    </style>
</head>
<body>

<header>
    <h1>Efeito Estufa Interativo</h1>
</header>

<nav>
    <a href="#causas">Causas</a>
    <a href="#consequencias">Consequências</a>
    <a href="#gases">Gases</a>
</nav>

<section id="causas">
    <h2>Causas do Efeito Estufa</h2>
    <p>O aumento de gases na atmosfera retém calor e provoca o efeito estufa. Principais causas:</p>
    <ul>
        <li>Queima de combustíveis fósseis (carvão, petróleo e gás natural).</li>
        <li>Desmatamento e queima de florestas.</li>
        <li>Atividades industriais e agrícolas.</li>
        <li>Emissões de veículos automotores.</li>
    </ul>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Smog_in_Los_Angeles.jpg/640px-Smog_in_Los_Angeles.jpg" alt="Poluição urbana">
</section>

<section id="consequencias">
    <h2>Consequências do Efeito Estufa</h2>
    <ul>
        <li>Aquecimento global e aumento da temperatura média da Terra.</li>
        <li>Derretimento das calotas polares e aumento do nível do mar.</li>
        <li>Alterações nos padrões de chuva e secas prolongadas.</li>
        <li>Impactos na biodiversidade e extinção de espécies.</li>
        <li>Eventos climáticos extremos, como furacões e tempestades intensas.</li>
    </ul>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Melting_Glacier.jpg/640px-Melting_Glacier.jpg" alt="Derretimento de geleiras">
</section>

<section id="gases">
    <h2>Gases do Efeito Estufa</h2>
    <p>Principais gases e suas fórmulas químicas:</p>
    <div class="chart-container">
        <div class="bar">
            <div data-height="30%"></div>
            <span>CO<sub>2</sub></span>
        </div>
        <div class="bar">
            <div data-height="20%"></div>
            <span>CH<sub>4</sub></span>
        </div>
        <div class="bar">
            <div data-height="10%"></div>
            <span>N<sub>2</sub>O</span>
        </div>
        <div class="bar">
            <div data-height="35%"></div>
            <span>H<sub>2</sub>O</span>
        </div>
        <div class="bar">
            <div data-height="5%"></div>
            <span>CFCs</span>
        </div>
    </div>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Greenhouse_gas_effect.svg/640px-Greenhouse_gas_effect.svg.png" alt="Diagrama do efeito estufa">
</section>

<footer>
    <p>&copy; 2025 Efeito Estufa Interativo - Educativo</p>
</footer>

<script>
    // Animação ao rolar
    const sections = document.querySelectorAll('section');
    const bars = document.querySelectorAll('.bar div');

    function checkVisibility() {
        const triggerBottom = window.innerHeight * 0.85;

        sections.forEach(section => {
            const sectionTop = section.getBoundingClientRect().top;
            if(sectionTop < triggerBottom) {
                section.classList.add('visible');
            }
        });

        bars.forEach(bar => {
            const barParentTop = bar.parentElement.getBoundingClientRect().top;
            if(barParentTop < triggerBottom) {
                bar.style.height = bar.getAttribute('data-height');
            }
        });
    }

    window.addEventListener('scroll', checkVisibility);
    window.addEventListener('load', checkVisibility);
</script>

</body>
</html>

