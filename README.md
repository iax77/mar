<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mensaje Especial</title>
    <style>
        body {
            background-color: #0f0f0f; /* Fondo oscuro */
            color: #d3d3d3; /* Texto gris claro */
            font-family: 'Courier New', Courier, monospace;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            text-align: center;
        }

        .content {
            max-width: 700px;
            margin: 0 auto;
            background-color: #2d2d2d; /* Fondo de la caja */
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
        }

        h1, h2 {
            color: #4CAF50;
        }

        #inputContainer {
            margin-top: 20px;
        }

        input {
            background-color: #1a1a1a;
            color: #fff;
            border: none;
            border-bottom: 2px solid #4CAF50;
            padding: 10px;
            font-size: 18px;
            width: 50%;
            margin-top: 20px;
            outline: none;
        }

        input:focus {
            border-bottom: 2px solid #77e177;
        }

        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            border-radius: 5px;
            margin-top: 10px;
        }

        button:hover {
            background-color: #45a049;
        }

        #message {
            margin-top: 20px;
            font-size: 20px;
            line-height: 1.6;
            display: none;
            text-align: left;
            white-space: pre-wrap;
        }
    </style>
</head>
<body>

    <div class="content">
        <h1>Accediendo al mensaje...</h1>
        <h2>Verificando...</h2>
        <h3>¿Quieres ver este mensaje?</h3>

        <div id="inputContainer">
            <input type="text" id="inputField" placeholder="Escribe 'yes' para ver el mensaje">
            <button onclick="checkInput()">Enviar</button>
        </div>

        <div id="message"></div>
    </div>

    <script>
        const messageText = `Hola, Mar.

Sé que no esperabas esto, pero quería hacer algo especial. ¡Feliz cumpleaños linda, ya son 21!!!!!!!!!!!!!!!!!!.

No sé de programación, pero quise intentarlo solo por ti. Porque si alguien merece algo especial, eres tú, además como me comentaste que vas a estar trabajando, maybe te haga sonreir un poquito JAJAJA.

Me gusta todo de ti, ¿sabias?. Tu forma de ser, tan suave que simplemente me pierdo en ti. La manera en que me tratas, cómo me miras, cómo me haces sentir… nunca había sentido algo así por alguien. Y no es solo porque eres bellisima (aunque lo eres, demasiado)………………. sino porque eres tú. Tu sonrisa, tu amabilidad, tu vulnerabilidad, las cosas que tú llamas defectos y que para mí son solo más razones para quererte. 

Todavía recuerdo la primera vez que te vi en cámara. Te tapabas mucho, la apagabas rápido, como si no quisieras que te viera. Y yo, en ese momento, me di cuenta de que si el mundo te viera como yo te veo, se enamoraría igual que yo lo hago cada vez que te miro.

ah, y claro está, nunca dejarás de ser mi gnomo, bueno mi oceano pacifico...

Espero que tengas un día muy lindo (como tu). 💚`;

        function checkInput() {
            var userInput = document.getElementById("inputField").value.toLowerCase();
            if (userInput === "yes") {
                document.getElementById("inputContainer").style.display = "none";
                showMessage(messageText);
            } else {
                alert("Solo puedes acceder si escribes 'yes'.");
            }
        }

        function showMessage(message) {
            let i = 0;
            const messageDiv = document.getElementById("message");
            messageDiv.style.display = "block";
            messageDiv.innerHTML = "";  // Clear message initially
            
            function typeWriter() {
                if (i < message.length) {
                    messageDiv.innerHTML += message.charAt(i);
                    i++;
                    setTimeout(typeWriter, 50);  // Adjust typing speed here
                }
            }

            typeWriter();
        }
    </script>

</body>
</html>
