<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Terminal</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

        body {
            background-color: #000;
            color: #fff;
            font-family: 'Press Start 2P', monospace;
            margin: 0;
            padding: 20px;
            font-size: 16px;
            text-transform: uppercase;
        }

        #terminal {
            max-width: 900px;
            margin: auto;
            white-space: pre-wrap;
            word-wrap: break-word;
            padding: 20px;
            line-height: 1.6;
        }

        .hidden {
            display: none;
        }

        .input-line {
            display: flex;
            align-items: center;
        }

        .prompt {
            color: #fff;
            font-weight: bold;
            margin-right: 10px;
        }

        .input-field {
            background: none;
            border: none;
            color: #fff;
            font-family: 'Press Start 2P', monospace;
            font-size: 16px;
            outline: none;
            width: 300px;
            text-transform: uppercase;
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
    </style>
</head>
<body>

    <div id="terminal">
        <div id="intro"></div>

        <div id="inputContainer" class="input-line">
            <span class="prompt">USER@SYSTEM:~$</span>
            <input type="text" id="inputField" class="input-field" autofocus>
            <span class="blinking-cursor"></span>
        </div>

        <div id="message" class="hidden"></div>
    </div>

    <script>
        const introText = `INITIALIZING SYSTEM...
LOADING SECURE CONNECTION...
VERIFYING IDENTITY...
ACCESS GRANTED.

HI MAR, THERE'S SOMETHING SPECIAL I WANT TO SHARE WITH YOU. 
ONCE YOU SAY 'YES,' THERE'S NO GOING BACK. ARE YOU SURE? (YES/NO)
`;

        const messageText = `HOLA, MAR.

SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!!!!!!!!!!!!!!!!!!.

NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ, ADEMÁS COMO ME COMENTASTE QUE VAS A ESTAR TRABAJANDO, MAYBE TE HAGA SONREÍR UN POQUITO JAJAJA.

ME GUSTA TODO DE TI, ¿SABÍAS?. TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI. LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN. Y NO ES SOLO PORQUE ERES BELLÍSIMA (AUNQUE LO ERES, DEMASIADO)………………. SINO PORQUE ERES TÚ. TU SONRISA, TU AMABILIDAD, TU VULNERABILIDAD, LAS COSAS QUE TÚ LLAMAS DEFECTOS Y QUE PARA MÍ SON SOLO MÁS RAZONES PARA QUERERTE. 

TODAVÍA RECUERDO LA PRIMERA VEZ QUE TE VI EN CÁMARA. TE TAPABAS MUCHO, LA APAGABAS RÁPIDO, COMO SI NO QUISIERAS QUE TE VIERA. Y YO, EN ESE MOMENTO, ME DI CUENTA DE QUE SI EL MUNDO TE VIERA COMO YO TE VEO, SE ENAMORARÍA IGUAL QUE YO LO HAGO CADA VEZ QUE TE MIRO.

AH, Y CLARO ESTÁ, NUNCA DEJARÁS DE SER MI GNOMO, BUENO MI OCÉANO PACÍFICO...

ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚`;

        function typeWriterEffect(element, text, speed = 30, callback = null) {
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
                    document.getElementById("inputContainer").style.display = "none";
                    let messageDiv = document.getElementById("message");
                    messageDiv.classList.remove("hidden");
                    typeWriterEffect(messageDiv, messageText, 30);
                } else {
                    document.getElementById("inputField").value = "";
                    alert("ACCESS DENIED. ONLY 'YES' IS ALLOWED.");
                }
            }
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);
        
        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40);
    </script>

</body>
</html>
        document.getElementById("inputField").addEventListener("keypress", checkInput);
        
        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40);
    </script>

</body>
</html>
