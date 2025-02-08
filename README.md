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
            width: 80px;
            text-transform: lowercase;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        .blink-button {
            font-family: 'Press Start 2P', cursive;
            font-size: 12px;
            background-color: #fff;
            color: #000;
            text-decoration: none;
            padding: 10px 20px;
            margin-top: 10px;
            border: none;
            cursor: pointer;
            animation: blink 1s infinite;
        }
    </style>
</head>
<body>

    <div id="terminal">
        <div id="intro" class="system-text"></div>

        <div id="promptText" class="fnaf-text hidden">
            <span id="typePrompt"></span>
            <div class="input-line hidden" id="inputContainer">
                (yes/no): <input type="text" id="inputField" class="input-field" autofocus>
            </div>
        </div>

        <div id="musicPrompt" class="hidden fnaf-text">
            Antes de empezar, me gustaría que reproduzcas esto: <br>
            <a href="https://open.spotify.com/track/3H9GcHKKJyZ9TEOLKlJ1U5?si=06pFZspsR_m7NuG9cXZ9ag" target="_blank">🎵 Escuchar canción 🎵</a>
            <br><br>
            <button class="blink-button" onclick="startMessage()">Ya puse la canción</button>
        </div>

        <div id="message" class="hidden fnaf-text"></div>
    </div>

    <script>
        const introText = `Initializing system...
Loading secure connection...
Verifying identity...
Access granted.\n\n`;

        const promptMessage = `Hi Mar, there's something special I want to share with you.\nOnce you say 'yes,' there's no going back.\nAre you sure?\n\n`;

        const messageText = `HOLA, MAR.

SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!!!!!!!!!!!!!

NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ.

ME GUSTA TODO DE TI, ¿SABÍAS? TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI. 
LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.

TODAVÍA RECUERDO LA PRIMERA VEZ QUE TE VI EN CÁMARA. TE TAPABAS MUCHO, LA APAGABAS RÁPIDO, COMO SI NO QUISIERAS QUE TE VIERA. Y YO, EN ESE MOMENTO, ME DI CUENTA DE QUE SI EL MUNDO TE VIERA COMO YO TE VEO, SE ENAMORARÍA IGUAL QUE YO LO HAGO CADA VEZ QUE TE MIRO.

ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚`;

        const finalMessageText = `\n\nPS: aquí hay otra sorpresa…\n`;

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
                document.getElementById("inputField").value = ""; // Limpiar input antes de continuar

                if (userInput === "yes") {
                    document.getElementById("promptText").style.display = "none";
                    document.getElementById("musicPrompt").classList.remove("hidden");
                } else {
                    alert("ACCESS DENIED. ONLY 'YES' IS ALLOWED.");
                }
            }
        }

        function showFinalMessage() {
            let messageDiv = document.getElementById("message");
            typeWriterEffect(messageDiv, finalMessageText, 50, function() {
                let buttonDiv = document.createElement("div");
                buttonDiv.innerHTML = `<a href="https://www.canva.com/design/DAGecp8p3NU/GW0duxMbLw8a3pVFDkE9Pg/edit?utm_content=DAGecp8p3NU&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton" target="_blank" class="blink-button">Entra aquí</a>`;
                messageDiv.appendChild(buttonDiv);
            });
        }

        function startMessage() {
            document.getElementById("musicPrompt").style.display = "none";
            let messageDiv = document.getElementById("message");
            messageDiv.classList.remove("hidden");
            typeWriterEffect(messageDiv, messageText, 50, showFinalMessage);
        }

        document.getElementById("inputField").addEventListener("keydown", checkInput);

        function startIntro() {
            let introDiv = document.getElementById("intro");
            typeWriterEffect(introDiv, introText, 40, function() {
                document.getElementById("promptText").classList.remove("hidden");
                let promptDiv = document.getElementById("typePrompt");
                typeWriterEffect(promptDiv, promptMessage, 40, function() {
                    document.getElementById("inputContainer").classList.remove("hidden");
                });
            });
        }

        startIntro();
    </script>

</body>
</html>
