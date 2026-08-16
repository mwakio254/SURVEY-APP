<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Survey App</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 20px;
      text-align: center;
    }

    .container {
      max-width: 600px;
      margin: 30px auto;
      background: white;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 3px 10px rgba(0,0,0,0.15);
    }

    h1 {
      color: #222;
    }

    button {
      width: 100%;
      padding: 15px;
      margin: 10px 0;
      border: none;
      border-radius: 8px;
      background: #1877f2;
      color: white;
      font-size: 17px;
      cursor: pointer;
    }

    button:hover {
      background: #0d5dcc;
    }

    .answer {
      background: #eee;
      color: #222;
    }

    .answer:hover {
      background: #ddd;
    }

    #quiz,
    #result {
      display: none;
    }

    #score {
      font-size: 20px;
      font-weight: bold;
    }
  </style>
</head>

<body>

  <div class="container">

    <!-- HOME -->
    <div id="home">
      <h1>SURVEY-APP</h1>
      <p>Paid quiz and survey application</p>

      <button onclick="startQuiz()">Start Quiz</button>
    </div>

    <!-- QUIZ -->
    <div id="quiz">
      <h2 id="question"></h2>

      <button class="answer" onclick="answerQuestion(0)" id="answer0"></button>
      <button class="answer" onclick="answerQuestion(1)" id="answer1"></button>
      <button class="answer" onclick="answerQuestion(2)" id="answer2"></button>
      <button class="answer" onclick="answerQuestion(3)" id="answer3"></button>

      <p id="score">Points: 0</p>
    </div>

    <!-- RESULT -->
    <div id="result">
      <h1>Quiz Complete 🎉</h1>

      <p>Your final score is:</p>

      <h2 id="finalScore"></h2>

      <button onclick="startQuiz()">Play Again</button>

      <button onclick="goHome()">Home</button>
    </div>

  </div>

  <script>

    const questions = [

      {
        question: "What is the capital city of Kenya?",
        answers: ["Mombasa", "Nairobi", "Kisumu", "Nakuru"],
        correct: 1
      },

      {
        question: "Which planet is known as the Red Planet?",
        answers: ["Earth", "Mars", "Jupiter", "Venus"],
        correct: 1
      },

      {
        question: "How many days are in a week?",
        answers: ["5", "6", "7", "8"],
        correct: 2
      },

      {
        question: "What is 10 + 5?",
        answers: ["12", "15", "20", "25"],
        correct: 1
      },

      {
        question: "Which animal is known as the King of the Jungle?",
        answers: ["Elephant", "Lion", "Tiger", "Giraffe"],
        correct: 1
      }

    ];

    let currentQuestion = 0;
    let points = 0;

    function startQuiz() {

      currentQuestion = 0;
      points = 0;

      document.getElementById("home").style.display = "none";
      document.getElementById("result").style.display = "none";
      document.getElementById("quiz").style.display = "block";

      showQuestion();
    }

    function showQuestion() {

      const q = questions[currentQuestion];

      document.getElementById("question").innerText =
        "Question " + (currentQuestion + 1) +
        " of " + questions.length + ": " +
        q.question;

      document.getElementById("answer0").innerText = q.answers[0];
      document.getElementById("answer1").innerText = q.answers[1];
      document.getElementById("answer2").innerText = q.answers[2];
      document.getElementById("answer3").innerText = q.answers[3];

      document.getElementById("score").innerText =
        "Points: " + points;
    }

    function answerQuestion(answer) {

      const q = questions[currentQuestion];

      if (answer === q.correct) {
        points += 10;
        alert("Correct! +10 points 🎉");
      } else {
        alert("Wrong answer ❌");
      }

      currentQuestion++;

      if (currentQuestion >= questions.length) {
        finishQuiz();
      } else {
        showQuestion();
      }
    }

    function finishQuiz() {

      document.getElementById("quiz").style.display = "none";
      document.getElementById("result").style.display = "block";

      document.getElementById("finalScore").innerText =
        points + " points";
    }

    function goHome() {

      document.getElementById("result").style.display = "none";
      document.getElementById("home").style.display = "block";
    }

  </script>

</body>
</html>
