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

        /* Animación de Spider-Man */
        #spiderman {
            position: absolute;
            top: -200px;
            left: 50%;
            transform: translateX(-50%);
            width: 150px;
            height: auto;
            opacity: 0;
        }

        .falling {
            animation: fall 2s ease-out forwards;
        }

        @keyframes fall {
            0% { top: -200px; opacity: 0; }
            100% { top: 50%; opacity: 1; }
        }

        /* Caja de pizza */
        #pizza-box {
            position: absolute;
            top: 55%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 200px;
            height: 150px;
            background: #d2691e;
            border: 3px solid #8b4513;
            display: none;
            text-align: center;
            padding: 10px;
        }

        #note {
            font-family: 'VT323', monospace;
            font-size: 18px;
            background: white;
            padding: 5px;
            margin-top: 10px;
            text-align: center;
            transform: rotate(-10deg);
            display: inline-block;
            position: relative;
        }

        #note span {
            text-decoration: line-through;
            color: red;
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
            <input type="text" id="inputField" class="input-field" autofocus>
        </div>

        <div id="musicPrompt" class="hidden fnaf-text">
            Antes de empezar, me gustaría que reproduzcas esto: <br>
            <a href="https://open.spotify.com/track/3H9GcHKKJyZ9TEOLKlJ1U5?si=06pFZspsR_m7NuG9cXZ9ag" target="_blank">🎵 Escuchar canción 🎵</a>
            <br><br>
            <button class="button" onclick="startAnimation()">Ya puse la canción</button>
        </div>

        <img id="spiderman" src="https://upload.wikimedia.org/wikipedia/en/0/0f/Spider-Man_-_Miles_Morales.png" alt="Spider-Man">
        
        <div id="pizza-box">
            <p>🍕 Para Mar 🍕</p>
            <div id="note">
                Para: <span>Pete</span> Spider-Man
            </div>
        </div>

        <div id="message" class="hidden fnaf-text">
            <p>HOLA, MAR.</p>
            <p>SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!!!!!!!!!!!!!</p>
            <p>NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ.</p>
            <p>ME GUSTA TODO DE TI, ¿SABÍAS? TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI. 
            LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.</p>
            <p>ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚</p>
        </div>
    </div>

    <script>
        const introText = `Initializing system...
Loading secure connection...
Verifying identity...
Access granted.\n\n`;

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
                    alert("ACCESS DENIED. ONLY 'YES' IS ALLOWED.");
                }
            }
        }

        function startAnimation() {
            document.getElementById("musicPrompt").style.display = "none";
            let spiderman = document.getElementById("spiderman");
            spiderman.classList.add("falling");
            setTimeout(() => {
                document.getElementById("pizza-box").style.display = "block";
                setTimeout(() => {
                    document.getElementById("message").classList.remove("hidden");
                }, 2000);
            }, 2000);
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);
        
        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40, function() {
            document.getElementById("promptText").classList.remove("hidden");
        });

    </script>

</body>
</html>
