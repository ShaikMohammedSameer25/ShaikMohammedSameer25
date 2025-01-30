<!DOCTYPE html>
<html>
<head>
<title>Quiz Game</title>
<style>
body {
  font-family: sans-serif;
}
#quiz-container {
  width: 500px;
  margin: 50px auto;
  border: 1px solid #ccc;
  padding: 20px;
}
#scoreboard {
  text-align: center;
  margin-bottom: 20px; 
}
#question {
  font-size: 1.2em;
  margin-bottom: 10px;
}
.options-container { 
    margin-bottom: 10px; 
}
button {
  padding: 10px 20px;
  margin: 5px;
  cursor: pointer;
}
#result {
  margin-top: 20px;
  font-weight: bold;
}
</style>
</head>
<body>

<div id="scoreboard">
    <h2>Score: <span id="current-score">0</span></h2>
</div>

<div id="quiz-container">
  <h1>Quiz Game</h1>
  <div id="question"></div>
  <div id="options"></div>  
  <button id="submit-btn">Submit</button> <div id="result"></div>
</div>

<script>
const quizData = [
  {
    question: "What is the capital of France?",
    options: ["Berlin", "Paris", "Madrid", "Rome"],
    answer: "Paris"
  },
  {
    question: "What is 2 + 2?",
    options: ["3", "4", "5", "6"],
    answer: "4"
  },
  {
    question: "Who painted the Mona Lisa?",
    options: ["Michelangelo", "Leonardo da Vinci", "Raphael", "Donatello"],
    answer: "Leonardo da Vinci"
  }
];

let currentQuestion = 0;
let score = 0;
let selectedAnswer; 

const questionDiv = document.getElementById("question");
const optionsDiv = document.getElementById("options");
const resultDiv = document.getElementById("result");
const submitButton = document.getElementById("submit-btn");
const scoreDisplay = document.getElementById("current-score");

function loadQuestion() {
  const currentQuizData = quizData[currentQuestion];
  questionDiv.textContent = currentQuizData.question;

  optionsDiv.innerHTML = ""; 
  currentQuizData.options.forEach(option => {
    const button = document.createElement("button");
    button.textContent = option;
    button.addEventListener("click", () => {
        selectedAnswer = option; // Store selected answer
        // Visually indicate selection (optional):
        const buttons = optionsDiv.querySelectorAll('button');
        buttons.forEach(btn => btn.classList.remove('selected')); 
        button.classList.add('selected'); 
    });
    optionsDiv.appendChild(button);
  });
  submitButton.disabled = false; 
}

submitButton.addEventListener("click", () => checkAnswer());

function checkAnswer() {
    if (!selectedAnswer) {
        resultDiv.textContent = "Please select an answer.";
        return; // Don't proceed if no answer selected
    }

    const currentQuizData = quizData[currentQuestion];
    if (selectedAnswer === currentQuizData.answer) {
      score++;
      resultDiv.textContent = "Correct!";
      scoreDisplay.textContent = score; 
    } else {
      resultDiv.textContent = "Incorrect.";
    }
    submitButton.disabled = true; 
    selectedAnswer = null; 

    currentQuestion++;
    if (currentQuestion < quizData.length) {
      loadQuestion();
    } else {
      showResult();
    }
  }

function showResult() {
  questionDiv.textContent = "Quiz finished!";
  optionsDiv.innerHTML = "";
  resultDiv.textContent = `Your final score: ${score}`;
  submitButton.style.display = "none"; 
}

loadQuestion(); 
</script>

</body>
</html>
