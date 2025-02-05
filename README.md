<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Terminal</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono&display=swap');

        body {
            background-color: #0d1117;
            color: #c9d1d9;
            font-family: 'JetBrains Mono', monospace;
            margin: 0;
            padding: 20px;
        }

        #terminal {
            background-color: #161b22;
            border-radius: 6px;
            padding: 20px;
            max-width: 800px;
            margin: auto;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
        }

        .system-text {
            color: #8b949e;
            font-size: 14px;
        }

        .prompt {
            color: #58a6ff;
        }

        .input-field {
            background: none;
            border: none;
            color: #c9d1d9;
            font-family: 'JetBrains Mono', monospace;
            font-size: 14px;
            outline: none;
            width: 50px;
            text-transform: lowercase;
        }

        .blinking-cursor {
            display: inline-block;
            width: 8px;
            height: 16px;
            background-color: #c9d1d9;
            animation: blink 1s step-end infinite;
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>

    <div id="terminal">
        <div id="intro" class="system-text"></div>

        <div id="promptText" class="hidden">
            <span class="prompt">mar@github:~$</span> Hi Mar, there's something special I want to share with you.<br>
            <span class="prompt">mar@github:~$</span> Once you say 'yes,' there's no going back.<br>
            <span class="prompt">mar@github:~$</span> Are you sure? 
            <div class="input-line">
                (yes/no): <input type="text" id="inputField" class="input-field" autofocus>
                <span class="blinking-cursor"></span>
            </div>
        </div>

        <div id="message" class="hidden"></div>
    </div>

    <script>
        const introText = `mar@github:~$ Initializing system...\nmar@github:~$ Loading secure connection...\nmar@github:~$ Verifying identity...\nmar@github:~$ Access granted.\n\n`;

        const messageText = `HOLA, MAR.

SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!

NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ.

ME GUSTA TODO DE TI, ¿SABÍAS? TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI. 
LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.

TODAVÍA RECUERDO LA PRIMERA VEZ QUE TE VI EN CÁMARA. TE TAPABAS MUCHO, LA APAGABAS RÁPIDO, COMO SI NO QUISIERAS QUE TE VIERA. Y YO, EN ESE MOMENTO, ME DI CUENTA DE QUE SI EL MUNDO TE VIERA COMO YO TE VEO, SE ENAMORARÍA IGUAL QUE YO LO HAGO CADA VEZ QUE TE MIRO.

ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚`;

        function typeWriterEffect(element, text, speed = 40, callback = null) {
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
                    let messageDiv = document.getElementById("message");
                    messageDiv.classList.remove("hidden");
                    typeWriterEffect(messageDiv, messageText, 50);
                } else {
                    document.getElementById("inputField").value = "";
                    alert("ACCESS DENIED. ONLY 'YES' IS ALLOWED.");
                }
            }
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);

        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40, function() {
            document.getElementById("promptText").classList.remove("hidden");
        });
    </script>

</body>
</html>
