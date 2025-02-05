<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mensaje Especial</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;600&display=swap');

        body {
            margin: 0;
            padding: 0;
            background-color: #000;
            color: #fff;
            font-family: 'Montserrat', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            text-align: center;
        }

        .container {
            position: relative;
            width: 100%;
            height: 100%;
        }

        /* Spider-Man swinging */
        .spiderman {
            position: absolute;
            top: -150px;
            left: 50%;
            transform: translateX(-50%);
            width: 120px;
            animation: swing 2.5s ease-in-out forwards;
        }

        @keyframes swing {
            0% { top: -150px; }
            50% { top: 200px; }
            100% { top: 100px; }
        }

        /* Pizza Box */
        .pizza-box {
            position: absolute;
            bottom: -200px;
            left: 50%;
            transform: translateX(-50%);
            width: 150px;
            cursor: pointer;
            transition: bottom 1s ease-in-out;
        }

        .pizza-box.open {
            bottom: 50px;
        }

        /* Paper Message */
        .paper {
            position: absolute;
            bottom: -100%;
            left: 50%;
            transform: translateX(-50%);
            width: 220px;
            opacity: 0;
            transition: opacity 1s ease-in-out, bottom 1s ease-in-out;
        }

        .paper.show {
            bottom: 150px;
            opacity: 1;
        }

        /* Final message */
        .final-message {
            position: absolute;
            bottom: -100%;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(255, 255, 255, 0.9);
            color: #000;
            padding: 15px;
            border-radius: 10px;
            font-size: 18px;
            font-weight: 600;
            width: 280px;
            text-align: center;
            opacity: 0;
            transition: opacity 1s ease-in-out, bottom 1s ease-in-out;
        }

        .final-message.show {
            bottom: 80px;
            opacity: 1;
        }
    </style>
</head>
<body>

    <div class="container">
        <img src="https://i.imgur.com/BS3vUiw.png" alt="Spider-Man" class="spiderman">
        <img src="https://i.imgur.com/UuZUwM4.png" alt="Pizza Box" class="pizza-box" id="pizzaBox">
        <img src="https://i.imgur.com/Zs4JtEV.png" alt="Paper Message" class="paper" id="paperMessage">  
        <div class="final-message" id="finalMessage">  
            Con todo lo que tengo, X.
        </div>
    </div>

    <script>
        document.getElementById("pizzaBox").addEventListener("click", function() {
            this.classList.add("open");
            document.getElementById("paperMessage").classList.add("show");

            setTimeout(function() {
                document.getElementById("finalMessage").classList.add("show");
            }, 2000);
        });
    </script>

</body>
</html>
