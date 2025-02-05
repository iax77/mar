<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Terminal</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323&display=swap');

        body {
            background-color: #000;
            color: #fff;
            margin: 0;
            padding: 20px;
            font-size: 14px;
            line-height: 1.6;
            text-align: center;
        }

        #terminal {
            max-width: 800px;
            margin: auto;
            padding: 20px;
            white-space: pre-wrap;
            word-wrap: break-word;
        }

        .system-text {
            font-family: 'VT323', monospace;
            font-size: 18px;
        }

        .fnaf-text {
            font-family: 'Press Start 2P', cursive;
            font-size: 14px;
        }

        .hidden {
            display: none;
        }

        .input-line {
            display: inline-block;
        }

        .prompt {
            font-family: 'Press Start 2P', cursive;
            color: #fff;
            margin-right: 5px;
        }

        .input-field {
            background: none;
            border: none;
            color: #fff;
            font-family: 'Press Start 2P', cursive;
            font-size: 14px;
            outline: none;
            width: 50px;
            text-transform: lowercase;
        }

        .blinking-cursor {
            display: inline-block;
            width: 10px;
            height: 18px;
            background-color: #fff;
            animation: blink 1s step-end infinite;
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        .question {
            font-family: 'Press Start 2P', cursive;
            color: #fff;
            margin-top: 20px;
        }

        .question input {
            margin-left: 10px;
        }

    </style>
</head>
<body>

    <div id="terminal">
        <div id="intro" class="system-text"></div>

        <div id="promptText" class="fnaf-text hidden">
            Hi Mar, there's something special I want to share with you. <br>
            Once you say 'yes,' there's no going back. <br>
            Are you sure? 
            <div class="input-line">
                (yes/no): <input type="text" id="inputField" class="input-field" autofocus>
                <span class="blinking-cursor"></span>
            </div>
        </div>

        <div id="game" class="hidden question">
            <p>¿Estás lista para jugar un juego? Responde a las siguientes preguntas para continuar:</p>
            <p>1. ¿Qué es lo que más te gusta hacer cuando no estás trabajando? (Escribe tu respuesta)</p>
            <input type="text" id="question1" class="input-field">
            <br><br>
            <p>2. ¿Qué película de Marvel es tu favorita? (Escribe tu respuesta)</p>
            <input type="text" id="question2" class="input-field">
            <br><br>
            <p>3. ¿Cuál es tu plato favorito de pasta? (Escribe tu respuesta)</p>
            <input type="text" id="question3" class="input-field">
            <br><br>
            <p>Cuando hayas respondido, presiona 'Enter' para continuar.</p>
        </div>

        <div id="message" class="hidden fnaf-text"></div>
    </div>

    <script>
        const introText = `Initializing system...
Loading secure connection...
Verifying identity...
Access granted.\n\n`;

        const promptText = `Hi Mar, there's something special I want to share with you.
Once you say 'yes,' there's no going back.
Are you sure? `;

        const messageText = `HOLA, MAR.

SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!

NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ.

ME GUSTA TODO DE TI, ¿SABÍAS? TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI. 
LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.

TODAVÍA RECUERDO LA PRIMERA VEZ QUE TE VI EN CÁMARA. TE TAPABAS MUCHO, LA APAGABAS RÁPIDO, COMO SI NO QUISIERAS QUE TE VIERA. Y YO, EN ESE MOMENTO, ME DI CUENTA DE QUE SI EL MUNDO TE VIERA COMO YO TE VEO, SE ENAMORARÍA IGUAL QUE YO LO HAGO CADA VEZ QUE TE MIRO.

ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚

CANTARES 1:16  
"¡CUÁN HERMOSA ERES, AMADA MÍA! ¡ERES UN ENCANTO!"`;

        function typeWriterEffect(element, text, speed = 50, callback = null) {
            let i = 0;
            function type() {
                if (i < text.length) {
                    element.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, speed);
                } else if (callback) {
                    callback();
                }
            }
            type();
        }

        function checkInput(event) {
            if (event.key === "Enter") {
                let userInput = document.getElementById("inputField").value.toLowerCase();
                if (userInput === "yes") {
                    document.getElementById("promptText").style.display = "none";
                    let gameDiv = document.getElementById("game");
                    gameDiv.classList.remove("hidden");
                } else {
                    document.getElementById("inputField").value = "";
                    alert("ACCESS DENIED. ONLY 'YES' IS ALLOWED.");
                }
            }
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);

        function checkAnswers() {
            const answer1 = document.getElementById("question1").value.toLowerCase();
            const answer2 = document.getElementById("question2").value.toLowerCase();
            const answer3 = document.getElementById("question3").value.toLowerCase();

            if (answer1 && answer2 && answer3) {
                let messageDiv = document.getElementById("message");
                messageDiv.classList.remove("hidden");
                typeWriterEffect(messageDiv, messageText, 50);
            } else {
                alert("Por favor, responde todas las preguntas.");
            }
        }

        const gameInputs = document.querySelectorAll('.input-field');
        gameInputs.forEach(input => {
            input.addEventListener('keypress', (event) => {
                if (event.key === "Enter") {
                    checkAnswers();
                }
            });
        });

        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40, function() {
            document.getElementById("promptText").classList.remove("hidden");
        });
    </script>

</body>
</html>
