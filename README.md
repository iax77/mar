<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mensaje Especial</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      color: #333;
      padding: 20px;
      text-align: center;
    }
    .hidden {
      display: none;
    }
    .message {
      font-size: 18px;
      margin-top: 20px;
      font-weight: bold;
    }
    .question {
      font-size: 20px;
      margin: 20px 0;
    }
    .question input {
      padding: 10px;
      font-size: 16px;
      margin-top: 10px;
    }
    .message-block {
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <h1>¡Feliz Cumpleaños, Mar! 🎉</h1>
  
  <p>Para empezar, por favor escucha esta canción mientras te preparo algo especial para ti. Haz clic en el enlace:</p>
  
  <a href="https://open.spotify.com/track/3H9GcHKKJyZ9TEOLKlJ1U5?si=06pFZspsR_m7NuG9cXZ9ag" target="_blank">
    <button>Escucha la canción</button>
  </a>

  <div class="question hidden" id="q1">
    <p>¿Cuál es tu comida favorita?</p>
    <input type="text" id="answer1">
    <button onclick="checkAnswer(1)">Responder</button>
  </div>

  <div class="question hidden" id="q2">
    <p>¿Qué flor te gusta más?</p>
    <input type="text" id="answer2">
    <button onclick="checkAnswer(2)">Responder</button>
  </div>

  <div class="question hidden" id="q3">
    <p>¿Qué superhéroe de Marvel te gusta más?</p>
    <input type="text" id="answer3">
    <button onclick="checkAnswer(3)">Responder</button>
  </div>

  <div class="question hidden" id="q4">
    <p>¿Cuál es tu película favorita de Marvel?</p>
    <input type="text" id="answer4">
    <button onclick="checkAnswer(4)">Responder</button>
  </div>

  <div class="question hidden" id="q5">
    <p>¿De qué color es tu tulipán favorito?</p>
    <input type="text" id="answer5">
    <button onclick="checkAnswer(5)">Responder</button>
  </div>

  <div class="message-block hidden" id="message">
    <p>HOLA, MAR.</p>
    <p>SÉ QUE NO ESPERABAS ESTO, PERO QUERÍA HACER ALGO ESPECIAL. ¡FELIZ CUMPLEAÑOS LINDA, YA SON 21!</p>
    <p>NO SÉ DE PROGRAMACIÓN, PERO QUISE INTENTARLO SOLO POR TI. PORQUE SI ALGUIEN MERECE ALGO ESPECIAL, ERES TÚ.</p>
    <p>ME GUSTA TODO DE TI, ¿SABÍAS? TU FORMA DE SER, TAN SUAVE QUE SIMPLEMENTE ME PIERDO EN TI.</p>
    <p>LA MANERA EN QUE ME TRATAS, CÓMO ME MIRAS, CÓMO ME HACES SENTIR… NUNCA HABÍA SENTIDO ALGO ASÍ POR ALGUIEN.</p>
    <p>TODAVÍA RECUERDO LA PRIMERA VEZ QUE TE VI EN CÁMARA. TE TAPABAS MUCHO, LA APAGABAS RÁPIDO, COMO SI NO QUISIERAS QUE TE VIERA. Y YO, EN ESE MOMENTO, ME DI CUENTA DE QUE SI EL MUNDO TE VIERA COMO YO TE VEO, SE ENAMORARÍA IGUAL QUE YO LO HAGO CADA VEZ QUE TE MIRO.</p>
    <p>ESPERO QUE TENGAS UN DÍA MUY LINDO (COMO TÚ). 💚</p>
    <p><i>Cantar de los Cantares 1:16</i></p>
  </div>

  <script>
    function checkAnswer(questionNumber) {
      let answer = document.getElementById(`answer${questionNumber}`).value.toLowerCase();
      let correctAnswers = [
        "pasta", // Respuesta correcta para la pregunta 1
        "tulipan", // Respuesta correcta para la pregunta 2
        "spiderman", // Respuesta correcta para la pregunta 3
        "infinity war", // Respuesta correcta para la pregunta 4
        "tulipan" // Respuesta correcta para la pregunta 5
      ];

      if (answer.includes(correctAnswers[questionNumber - 1])) {
        document.getElementById(`q${questionNumber}`).classList.add('hidden');
        if (questionNumber < 5) {
          document.getElementById(`q${questionNumber + 1}`).classList.remove('hidden');
        } else {
          document.getElementById('message').classList.remove('hidden');
        }
      } else {
        alert('Respuesta incorrecta, intenta de nuevo.');
      }
    }

    document.getElementById('q1').classList.remove('hidden');
  </script>

</body>
</html>
