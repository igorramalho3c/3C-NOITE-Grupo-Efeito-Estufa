<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Efeito Estufa - Apresentação</title>
<style>
    body, html {
        margin: 0;
        padding: 0;
        font-family: 'Arial', sans-serif;
        overflow: hidden;
    }

    .slide {
        width: 100vw;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        transition: all 0.8s ease;
        position: absolute;
        top: 0;
        left: 0;
        opacity: 0;
        transform: scale(0.95);
    }

    .slide.active {
        opacity: 1;
        transform: scale(1);
        z-index: 1;
    }

    h1, h2 {
        margin: 20px 0;
    }

    p, ul {
        max-width: 700px;
        font-size: 1.2rem;
        line-height: 1.5;
    }

    ul {
        list-style: disc;
        text-align: left;
        margin: 20px auto;
        padding-left: 20px;
    }

    .buttons {
        position: absolute;
        bottom: 30px;
        display: flex;
        gap: 20px;
    }

    button {
        padding: 10px 20px;
        font-size: 1rem;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        background-color: #4CAF50;
        color: white;
        transition: 0.3s;
    }

    button:hover {
        background-color: #388E3C;
    }

    /* Gráfico de barras */
    .chart {
        display: flex;
        justify-content: center;
        align-items: flex-end;
        margin-top: 20px;
        gap: 20px;
    }

    .bar {
        width: 60px;
        background-color: #4CAF50;
        border-radius: 5px 5px 0 0;
        transition: height 1.5s ease;
        display: flex;
        justify-content: center;
        align-items: flex-end;
        color: white;
        font-weight: bold;
    }

    /* Cores diferentes por slide */
    #slide1 { background-color: #f0f8ff; color: #004d40; }
    #slide2 { background-color: #fff3e0; color: #e65100; }
    #slide3 { background-color: #e8f5e9; color: #1b5e20; }
    #slide4 { background-color: #f3e5f5; color: #4a148c; }
    #slide5 { background-color: #e1f5fe; color: #01579b; }

    img {
        max-width: 60%;
        border-radius: 10px;
        margin-top: 20px;
        transition: transform 0.3s;
    }

    img:hover {
        transform: scale(1.05);
    }
</style>
</head>
<body>

<!-- Slide 1 -->
<section class="slide active" id="slide1">
    <h1>Efeito Estufa</h1>
    <p>Aprenda sobre o efeito estufa, suas causas, consequências e como reduzir seu impacto.</p>
</section>

<!-- Slide 2 -->
<section class="slide" id="slide2">
    <h2>Causas do Efeito Estufa</h2>
    <ul>
        <li>Queima de combustíveis fósseis</li>
        <li>Desmatamento e queimadas</li>
        <li>Atividades industriais e agrícolas</li>
        <li>Emissões de veículos</li>
    </ul>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Smog_in_Los_Angeles.jpg/640px-Smog_in_Los_Angeles.jpg" alt="Poluição urbana">
</section>

<!-- Slide 3 -->
<section class="slide" id="slide3">
    <h2>Consequências</h2>
    <ul>
        <li>Aquecimento global</li>
        <li>Derretimento de geleiras e aumento do nível do mar</li>
        <li>Alterações climáticas e secas prolongadas</li>
        <li>Perda de biodiversidade</li>
        <li>Eventos extremos, como furacões</li>
    </ul>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Melting_Glacier.jpg/640px-Melting_Glacier.jpg" alt="Derretimento de geleiras">
</section>

<!-- Slide 4 -->
<section class="slide" id="slide4">
    <h2>Gases do Efeito Estufa</h2>
    <div class="chart">
        <div class="bar" data-height="70%">CO<sub>2</sub></div>
        <div class="bar" data-height="50%">CH<sub>4</sub></div>
        <div class="bar" data-height="30%">N<sub>2</sub>O</div>
        <div class="bar" data-height="35%">H<sub>2</sub>O</div>
        <div class="bar" data-height="10%">CFCs</div>
    </div>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Greenhouse_gas_effect.svg/640px-Greenhouse_gas_effect.svg.png" alt="Diagrama do efeito estufa">
</section>

<!-- Slide 5 -->
<section class="slide" id="slide5">
    <h2>Como reduzir?</h2>
    <ul>
        <li>Reduzir emissão de gases</li>
        <li>Usar energia renovável</li>
        <li>Preservar florestas</li>
        <li>Economizar energia e água</li>
    </ul>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/Solar_panels_in_field.jpg/640px-Solar_panels_in_field.jpg" alt="Energia renovável">
</section>

<!-- Navegação -->
<div class="buttons">
    <button id="prev">Anterior</button>
    <button id="next">Próximo</button>
</div>

<script>
    const slides = document.querySelectorAll('.slide');
    let current = 0;

    const bars = document.querySelectorAll('.bar');

    function showSlide(index) {
        slides.forEach((s, i) => {
            s.classList.remove('active');
            if(i === index) s.classList.add('active');
        });

        // Animar barras apenas no slide 4
        if(slides[index].id === 'slide4') {
            bars.forEach(bar => {
                bar.style.height = bar.getAttribute('data-height');
            });
        } else {
            bars.forEach(bar => bar.style.height = "0");
        }
    }

    document.getElementById('next').addEventListener('click', () => {
        current = (current + 1) % slides.length;
        showSlide(current);
    });

    document.getElementById('prev').addEventListener('click', () => {
        current = (current - 1 + slides.length) % slides.length;
        showSlide(current);
    });

    // Ativar barras ao carregar slide inicial
    showSlide(current);
</script>

</body>
</html>

</script>

</body>
</html>

