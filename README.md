<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500&family=Great+Vibes&display=swap" rel="stylesheet">
    <title>Cartas de Amor</title>

    <style>
        body {
            margin: 0;
            background: #3b2b2b;
            font-family: 'Cinzel', serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            color: #f5e6c8;
            overflow: hidden;
        }

        .titulo {
            font-size: 22px;
            margin-bottom: 20px;
            text-align: center;
            padding: 0 10px;
        }

        /* ESCENA */
        .scene {
            position: relative;
            width: 300px;
            height: 200px;
            cursor: pointer;
        }

        /* SOBRE (BASE) */
        .envelope {
            position: absolute;
            width: 100%;
            height: 100%;
            background: #d4b483;
            bottom: 0;
            border: 2px solid #b89264;
            box-shadow: 0 10px 20px rgba(0,0,0,0.4);
            z-index: 4;
        }

        /* El pico del sobre (frente) */
        .envelope:before {
            content: "";
            position: absolute;
            z-index: 5;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-bottom: 100px solid #caa472;
            bottom: 0;
            left: -2px;
        }

        /* SOLAPA (FLAP) */
        .flap {
            position: absolute;
            width: 0;
            height: 0;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-top: 100px solid #c49a6c;
            top: 0;
            left: 0;
            transform-origin: top;
            transition: 0.6s ease-in-out;
            z-index: 6; /* Por encima de todo al estar cerrado */
        }

        /* SELLO */
        .seal {
            position: absolute;
            width: 44px;
            height: 44px;
            background: #8b1e1e;
            border-radius: 50%;
            top: 80px;
            left: calc(50% - 22px);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 18px;
            transition: 0.4s;
            z-index: 7;
            box-shadow: 0 2px 5px rgba(0,0,0,0.3);
        }

        /* CONTENEDOR DE LA CARTA (SLIDER) */
        .slider {
            position: absolute;
            width: 260px;
            height: 180px;
            left: 20px;
            top: 10px; 
            overflow: hidden;
            z-index: 2; /* Detrás del frente del sobre */
            opacity: 0;
            transition: 0.8s ease-in-out;
            transform: translateY(0); /* Posición inicial oculta */
        }

        .cards {
            display: flex;
            transition: 0.5s ease-in-out;
        }

        .letter {
            min-width: 260px;
            height: 180px;
            background: #f5e6c8;
            color: #3b2b2b;
            padding: 20px;
            box-sizing: border-box;
            font-family: 'Great Vibes', cursive;
            font-size: 22px;
            text-align: center;
            border: 1px solid #d8c39a;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* --- ESTADOS DE ANIMACIÓN --- */
        
        .open .flap {
            transform: rotateX(180deg);
            z-index: 1; /* Al abrirse, pasa atrás de la carta */
        }

        .open .seal {
            opacity: 0;
            transform: scale(0);
        }

        .open .slider {
            opacity: 1;
            transform: translateY(-120px); /* LA CARTA SUBE */
            z-index: 10; /* Se pone al frente de todo para poder leerla */
        }

        /* CONTROLES */
        .controls {
            margin-top: 140px; /* Espacio para que la carta no los tape al subir */
            display: flex;
            gap: 15px;
            z-index: 20;
        }

        button {
            padding: 10px 20px;
            border: none;
            background: #c49a6c;
            color: white;
            border-radius: 50px;
            font-size: 18px;
            cursor: pointer;
            box-shadow: 0 4px 0 #a37d53;
            transition: 0.2s;
        }

        button:active {
            transform: translateY(3px);
            box-shadow: 0 1px 0 #a37d53;
        }

        @media (max-width:500px){
            .scene { width: 260px; }
            .slider { width: 220px; left: 20px; }
            .letter { min-width: 220px; font-size: 18px; }
            .envelope:before { border-left: 130px solid transparent; border-right: 130px solid transparent; }
            .flap { border-left: 130px solid transparent; border-right: 130px solid transparent; }
        }
    </style>
</head>
<body>

<div class="titulo">¿Quieres saber lo mucho que te quiero? 💌</div>

<div class="scene" onclick="abrirCarta()" id="sobre">
    <div class="slider" id="slider">
        <div class="cards" id="cards">
            <div class="letter">Mi amor ❤️<br><br>Eres el niño más lindo de todos y me encanta que seas tú quien me tiene loquita de amor.</div>
            <div class="letter">Me encanta hablar contigo porque siempre logras hacerme sonreír 😊💗.</div>
            <div class="letter">Eres la razón por la que mis días son más bonitos amor 😻.</div>
            <div class="letter">Un mes siendo mi notificación bonita y siempre esperada 🙈💗.</div>
            <div class="letter">Tu forma de ser es lo que más me enamora y esos ojitos ni hablar 😻.</div>
            <div class="letter">Te elegiría mil veces, en esta y en la otra vida y hasta el infinito 💫.</div>
            <div class="letter">Gracias por hacerme feliz mi niñoo lindo 💙🩵.</div>
            <div class="letter">Te amo mas de lo que tu amas al Barca jaja 🙈💗.</div>
            <div class="letter">Contigo si a todo, eres lo que siempre desee 💗.</div>
            <div class="letter">Te amo muchísimo 😽❤️</div>
        </div>
    </div>

    <div class="envelope"></div>
    <div class="flap"></div>
    <div class="seal">❤</div>
</div>

<div class="controls">
    <button onclick="event.stopPropagation(); anterior()">⬅</button>
    <button onclick="event.stopPropagation(); siguiente()">➡</button>
</div>

<script>
    let index = 0;
    const cards = document.getElementById("cards");
    const total = document.querySelectorAll(".letter").length;

    // Ajuste dinámico del ancho para el desplazamiento
    function actualizar() {
        const width = document.querySelector('.letter').clientWidth;
        cards.style.transform = `translateX(-${index * width}px)`;
    }

    function siguiente() {
        index++;
        if(index >= total) index = 0;
        actualizar();
    }

    function anterior() {
        index--;
        if(index < 0) index = total - 1;
        actualizar();
    }

    function abrirCarta() {
        document.getElementById("sobre").classList.toggle("open");
    }
</script>

</body>
</html>
