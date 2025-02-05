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

        @keyframes pulse {
            0% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.2); opacity: 0.7; }
            100% { transform: scale(1); opacity: 1; }
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

        <div id="musicPrompt" class="hidden fnaf-text">
            Antes de empezar, me gustaría que reproduzcas esto: <br>
            <a href="https://open.spotify.com/track/3H9GcHKKJyZ9TEOLKlJ1U5?si=06pFZspsR_m7NuG9cXZ9ag" target="_blank">🎵 Escuchar canción 🎵</a>
            <br><br>
            <button class="button" onclick="startMessage()">Ya puse la canción</button>
        </div>

        <div id="message" class="hidden fnaf-text"></div>

        <audio id="audioMessage" controls class="hidden">
            <source src="tuMensajeDeVoz.mp3" type="audio/mp3">
            Tu navegador no soporta el elemento de audio.
        </audio>

    </div>

    <script>
        const introText = `Initializing system...
Loading secure connection...
Verifying identity...
Access granted.\n\n`;

        const messageText = `HOLA, MAR.

SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!!!!!!!!!!!!!

NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ.

ME GUSTA TODO DE TI, ¿SABÍAS? TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI. 
LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.

TODAVÍA RECUERDO LA PRIMERA VEZ QUE TE VI EN CÁMARA. TE TAPABAS MUCHO, LA APAGABAS RÁPIDO, COMO SI NO QUISIERAS QUE TE VIERA. Y YO, EN ESE MOMENTO, ME DI CUENTA DE QUE SI EL MUNDO TE VIERA COMO YO TE VEO, SE ENAMORARÍA IGUAL QUE YO LO HAGO CADA VEZ QUE TE MIRO.

ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚`;

PS: SI ESCRIBES AMOR EL FONDO CAMBIA A ROSA, YA SÉ QUE NO TE GUSTA EL ROSADO, PERO LA CANCIÓN SE LLAMA BACHATA ROSA Y TE LA DEDICO.



PS DEL PS: te quiero mucho mi niña, te mereces más <33333!!!!

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
                    document.body.style.backgroundColor = "#ff69b4";  // Cambiar fondo a rosa
                    let heart = document.createElement("div");
                    heart.innerHTML = "❤️";
                    heart.style.fontSize = "100px";
                    heart.style.position = "absolute";
                    heart.style.top = "50%";
                    heart.style.left = "50%";
                    heart.style.transform = "translate(-50%, -50%)";
                    heart.style.animation = "pulse 1.5s infinite";
                    document.body.appendChild(heart);
                } else {
                    document.getElementById("inputField").value = "";
                    alert("ACCESS DENIED. ONLY 'YES' IS ALLOWED.");
                }
            }
        }

        function startMessage() {
            document.getElementById("musicPrompt").style.display = "none";
            let messageDiv = document.getElementById("message");
            messageDiv.classList.remove("hidden");
            typeWriterEffect(messageDiv, messageText, 50, function() {
                playAudioMessage();  // Reproducir mensaje de voz al final
            });
        }

        function playAudioMessage() {
            let audio = document.getElementById("audioMessage");
            audio.play();
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);
        
        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40, function() {
            document.getElementById("promptText").classList.remove("hidden");
        });
    </script>

</body>
</html>
