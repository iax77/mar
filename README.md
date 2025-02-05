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
            text-align: center;
        }

        #terminal {
            max-width: 800px;
            margin: auto;
            padding: 20px;
        }

        .hidden {
            display: none;
        }

        .system-text {
            font-family: 'VT323', monospace;
            font-size: 18px;
        }

        .fnaf-text {
            font-family: 'Press Start 2P', cursive;
            font-size: 14px;
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
        }

    </style>
</head>
<body>

    <div id="terminal">
        <div id="loading" class="system-text"></div>

        <div id="promptText" class="fnaf-text hidden">
            Hi Mar, there's something special I want to share with you. <br>
            Once you say 'yes,' there's no going back. <br>
            Are you sure?  
            <br><br>
            (yes/no): <input type="text" id="inputField" class="input-field" autofocus>
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
        const introText = `Initializing system...\nLoading secure connection...\nVerifying identity...\nAccess granted.\n\n`;

        const messages = [
            { time: 0, text: "HOLA, MAR.\n\n" },
            { time: 10, text: "SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!\n\n" },
            { time: 30, text: "NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ.\n\n" },
            { time: 50, text: "ME GUSTA TODO DE TI, ¿SABÍAS? TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI.\n\n" },
            { time: 70, text: "LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.\n\n" },
            { time: 90, text: "TODAVÍA RECUERDO LA PRIMERA VEZ QUE TE VI EN CÁMARA. TE TAPABAS MUCHO, LA APAGABAS RÁPIDO, COMO SI NO QUISIERAS QUE TE VIERA.\n\n" },
            { time: 120, text: "Y YO, EN ESE MOMENTO, ME DI CUENTA DE QUE SI EL MUNDO TE VIERA COMO YO TE VEO, SE ENAMORARÍA IGUAL QUE YO LO HAGO CADA VEZ QUE TE MIRO.\n\n" },
            { time: 180, text: "ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚" }
        ];

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

            messages.forEach(msg => {
                setTimeout(() => {
                    typeWriterEffect(messageDiv, msg.text, 50);
                }, msg.time * 1000);
            });
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);
        
        let loadingDiv = document.getElementById("loading");
        typeWriterEffect(loadingDiv, introText, 40, function() {
            document.getElementById("promptText").classList.remove("hidden");
        });
    </script>

</body>
</html>
