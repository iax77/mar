<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Terminal</title>
    <style>
        body {
            background-color: #000;
            color: #33ff33;
            font-family: 'Courier New', Courier, monospace;
            margin: 0;
            padding: 20px;
            font-size: 18px;
        }

        #terminal {
            max-width: 800px;
            margin: auto;
            white-space: pre-wrap;
            word-wrap: break-word;
            padding: 20px;
        }

        .hidden {
            display: none;
        }

        .input-line {
            display: flex;
            align-items: center;
        }

        .prompt {
            color: #33ff33;
            margin-right: 10px;
        }

        .input-field {
            background: none;
            border: none;
            color: #33ff33;
            font-family: 'Courier New', Courier, monospace;
            font-size: 18px;
            outline: none;
            width: 300px;
        }

        .blinking-cursor {
            display: inline-block;
            width: 10px;
            height: 18px;
            background-color: #33ff33;
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
            <span class="prompt">user@system:~$</span>
            <input type="text" id="inputField" class="input-field" autofocus>
            <span class="blinking-cursor"></span>
        </div>

        <div id="message" class="hidden"></div>
    </div>

    <script>
        const introText = `Initializing system...
Loading secure connection...
Verifying identity...
Access granted.

Hi Mar, there's something special I want to share with you. 
Once you say 'yes,' there's no going back. Are you sure? (yes/no)
`;

        const messageText = `Hola, Mar.

Sé que no esperabas esto, pero quería hacer algo especial. ¡Feliz cumpleaños linda, ya son 21!!!!!!!!!!!!!!!!!!.

No sé de programación, pero quise intentarlo solo por ti. Porque si alguien merece algo especial, eres tú, además como me comentaste que vas a estar trabajando, maybe te haga sonreír un poquito JAJAJA.

Me gusta todo de ti, ¿sabias?. Tu forma de ser, tan suave que simplemente me pierdo en ti. La manera en que me tratas, cómo me miras, cómo me haces sentir… nunca había sentido algo así por alguien. Y no es solo porque eres bellísima (aunque lo eres, demasiado)………………. sino porque eres tú. Tu sonrisa, tu amabilidad, tu vulnerabilidad, las cosas que tú llamas defectos y que para mí son solo más razones para quererte. 

Todavía recuerdo la primera vez que te vi en cámara. Te tapabas mucho, la apagabas rápido, como si no quisieras que te viera. Y yo, en ese momento, me di cuenta de que si el mundo te viera como yo te veo, se enamoraría igual que yo lo hago cada vez que te miro.

ah, y claro está, nunca dejarás de ser mi gnomo, bueno mi océano pacífico...

Espero que tengas un día muy lindo (como tú). 💚`;

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
                    document.getElementById("inputContainer").style.display = "none";
                    let messageDiv = document.getElementById("message");
                    messageDiv.classList.remove("hidden");
                    typeWriterEffect(messageDiv, messageText, 50);
                } else {
                    document.getElementById("inputField").value = "";
                    alert("Access denied. Only 'yes' is allowed.");
                }
            }
        }

        document.getElementById("inputField").addEventListener("keypress", checkInput);
        
        let introDiv = document.getElementById("intro");
        typeWriterEffect(introDiv, introText, 40);
    </script>

</body>
</html>
