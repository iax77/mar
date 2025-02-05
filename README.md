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
            overflow: hidden;
        }

        #terminal {
            max-width: 800px;
            margin: auto;
            padding: 20px;
            white-space: pre-wrap;
            word-wrap: break-word;
            position: relative;
            z-index: 2;
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

        .button {
            font-family: 'Press Start 2P', cursive;
            font-size: 12px;
            background-color: #fff;
            color: #000;
            border: none;
            padding: 10px;
            margin-top: 10px;
            cursor: pointer;
            display: inline-block;
        }

        /* Portal místico */
        #portal {
            position: fixed;
            top: 50%;
            left: 50%;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(255,140,0,0.8) 10%, rgba(0,0,0,0) 70%);
            border-radius: 50%;
            transform: translate(-50%, -50%) scale(0);
            animation: portalAnimation 3s ease-out forwards;
            z-index: 1;
        }

        @keyframes portalAnimation {
            0% { transform: translate(-50%, -50%) scale(0); opacity: 0; }
            50% { transform: translate(-50%, -50%) scale(1.2); opacity: 1; }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 0; }
        }

        /* Magia del Caos */
        .chaos-magic {
            animation: chaosEffect 1.5s infinite alternate;
        }

        @keyframes chaosEffect {
            0% { text-shadow: 0 0 5px red, 0 0 10px red, 0 0 15px darkred; }
            100% { text-shadow: 0 0 10px darkred, 0 0 15px red, 0 0 20px crimson; }
        }

        /* Líneas doradas moviéndose en el fondo */
        .golden-lines::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://i.imgur.com/lJzvbPi.png'); /* Imagen de líneas mágicas */
            opacity: 0.2;
            animation: moveLines 10s linear infinite;
        }

        @keyframes moveLines {
            from { background-position: 0 0; }
            to { background-position: 100% 100%; }
        }

    </style>
</head>
<body class="golden-lines">

    <div id="portal"></div> <!-- Portal Místico -->

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

        <div id="musicPrompt" class="hidden fnaf-text">
            Antes de empezar, me gustaría que reproduzcas esto: <br>
            <a href="https://open.spotify.com/track/3H9GcHKKJyZ9TEOLKlJ1U5?si=06pFZspsR_m7NuG9cXZ9ag" target="_blank">🎵 Escuchar canción 🎵</a>
            <br><br>
            <button class="button" onclick="startMessage()">Ya puse la canción</button>
        </div>

        <div id="message" class="hidden fnaf-text"></div>

    </div>

    <script>
        const introText = `Initializing system...
Loading secure connection...
Verifying identity...
Access granted.\n\n`;

        const messageText = `HOLA, MAR.

SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!!!!!!!!!!!!!

ME GUSTA TODO DE TI. TU FORMA DE SER, CÓMO ME TRATAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.

ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚`;

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
                    document.getElementById("musicPrompt").classList.remove("hidden");
                } else if (userInput.includes("feliz") || userInput.includes("amor")) {
                    document.body.classList.add("chaos-magic");
                }
            }
        }

        function startMessage() {
            document.getElementById("musicPrompt").style.display = "none";
            let messageDiv = document.getElementById("message");
            messageDiv.classList.remove("hidden");
            typeWriterEffect(messageDiv, messageText, 50);
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);
        
        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40, function() {
            document.getElementById("promptText").classList.remove("hidden");
        });
    </script>

</body>
</html>
