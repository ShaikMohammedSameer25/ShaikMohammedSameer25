<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Game</title>
    <style>
        body {
            font-family: sans-serif;
            background: linear-gradient(to bottom right, #3498db, #e74c3c); /* Attractive gradient background */
            margin: 0; /* Remove default margins */
            display: flex;
            justify-content: center; /* Center horizontally */
            align-items: center; /* Center vertically */
            min-height: 100vh; /* Ensure full viewport height */
            color: white; /* Text color for contrast */
            overflow: hidden; /* Hide scrollbars if content overflows */
        }

        .container {
            background-color: rgba(255, 255, 255, 0.2); /* Semi-transparent white container */
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.3); /* Add a subtle shadow */
            text-align: center; /* Center text within the container */
        }

        h1 {
            color: #fff; /* White heading */
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3); /* Add a text shadow */
        }

        button {
            background-color: #2ecc71; /* Green button */
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
            transition: background-color 0.3s ease; /* Smooth transition for hover effect */
            box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.2);
        }

        button:hover {
            background-color: #27ae60; /* Darker green on hover */
        }

        /* Style for the quiz area (hidden initially) */
        #quiz-area {
            display: none; /* Initially hidden */
            margin-top: 20px;
        }

        /* Add more styles for questions, options, etc. as needed */
        .question {
            font-size: 20px;
            margin-bottom: 10px;
        }

        .options {
            display: flex;
            flex-direction: column; /* Stack options vertically */
            align-items: flex-start; /* Align options to the left */
        }

        .option {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Welcome to the Quiz!</h1>
        <button id="play-button">Play Now</button>

        <div id="quiz-area">
            <div class="question">What is the capital of France?</div>
            <div class="options">
                <label class="option"><input type="radio" name="q1" value="a"> Paris</label>
                <label class="option"><input type="radio" name="q1" value="b"> Rome</label>
                <label class="option"><input type="radio" name="q1" value="c"> Berlin</label>
            </div>
            </div>
    </div>

    <script>
        const playButton = document.getElementById('play-button');
        const quizArea = document.getElementById('quiz-area');

        playButton.addEventListener('click', () => {
            playButton.style.display = 'none'; // Hide the play button
            quizArea.style.display = 'block'; // Show the quiz area
        });

        // Add more JavaScript for quiz logic (questions, answers, scoring, etc.)
    </script>

</body>
</html>
//second page
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Game</title>
    <style>
        body {
            font-family: sans-serif;
            background-color: #3498db; 
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: white;
            overflow: hidden;
        }

        .container {
            background-color: rgba(255, 255, 255, 0.2);
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.3);
            text-align: center;
        }

        h1 {
            color: #fff;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        button {
            background-color: #2ecc71;
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.2);
            margin: 10px; 
        }

        button:hover {
            background-color: #27ae60;
        }

        #quiz-area {
            display: none;
            margin-top: 20px;
        }

        .question {
            font-size: 20px;
            margin-bottom: 10px;
        }

        .options {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
        }

        .option {
            margin-bottom: 10px;
        }

        #level-selection { 
            display: block; 
        }

        #quiz-area {
            display: none; 
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Welcome to the Quiz!</h1>
        <div id="level-selection">
            <h2>Select Difficulty Level:</h2>
            <button data-level="easy">Easy</button>
            <button data-level="medium">Medium</button>
            <button data-level="hard">Hard</button>
        </div>
        <div id="quiz-area">
            <div class="question"></div> <div class="options"></div>
            <button id="next-button">Next</button>
            <button id="submit-button" style="display:none;">Submit Quiz</button>
        </div>
    </div>
    <script>
        const levelSelection = document.getElementById('level-selection');
        const quizArea = document.getElementById('quiz-area');
        const questionElement = document.querySelector('.question');
        const optionsElement = document.querySelector('.options');
        const nextButton = document.getElementById('next-button');
        const submitButton = document.getElementById('submit-button');
        let currentLevel;
        let currentQuestionIndex = 0;
        let score = 0;

        const quizData = {
            easy: [
                { question: "What is 2 + 2?", options: ["3", "4", "5"], answer: "4" },
                { question: "What is the color of the sky?", options: ["Red", "Blue", "Green"], answer: "Blue" },
                
            ],
            medium: [
                { question: "What is the capital of France?", options: ["Berlin", "Paris", "Rome"], answer: "Paris" },
                { question: "What is the largest planet in our solar system?", options: ["Earth", "Jupiter", "Mars"], answer: "Jupiter" }              
            ],
            hard: [
                { question: "What is the speed of light?", options: ["299,792,458 m/s", "300,000 km/s", "100,000 mph"], answer: "299,792,458 m/s" },
                { question: "Who painted the Mona Lisa?", options: ["Michelangelo", "Leonardo da Vinci", "Raphael"], answer: "Leonardo da Vinci" }                
            ],
        };              levelSelection.querySelectorAll('button').forEach(button => {
            button.addEventListener('click', () => {
                currentLevel = button.dataset.level;
                levelSelection.style.display = 'none';
                quizArea.style.display = 'block';
                loadQuestion();
            });
        });
        function loadQuestion() {
            if (currentQuestionIndex < quizData[currentLevel].length) {
                const currentQuestion = quizData[currentLevel][currentQuestionIndex];
                questionElement.textContent = currentQuestion.question;
                optionsElement.innerHTML = ''; // Clear previous options
                currentQuestion.options.forEach(option => {
                    const label = document.createElement('label');
                    label.className = 'option';
                    const input = document.createElement('input');
                    input.type = 'radio';
                    input.name = 'answer'; // Important: Same name for radio group
                    input.value = option;
                    label.appendChild(input);                  label.appendChild(document.createTextNode(option));
                    optionsElement.appendChild(label);
                });
            } else {
                            showResults();
            }
        }
        nextButton.addEventListener('click', () => {
            const selectedOption = document.querySelector('input[name="answer"]:checked');
            if (selectedOption) {
                const userAnswer = selectedOption.value;
                const correctAnswer = quizData[currentLevel][currentQuestionIndex].answer;
                if (userAnswer === correctAnswer) {
                    score++;
                }
                currentQuestionIndex++;
                loadQuestion();
                if (currentQuestionIndex === quizData[currentLevel].length -1 ){
                    nextButton.style.display = 'none';
                    submitButton.style.display = 'block';
                }
            } else {
                alert("Please select an answer.");
            }
        });

        submitButton.addEventListener('click', showResults);

        function showResults() {
            quizArea.innerHTML = `<h2>Quiz Finished!</h2><p>Your score: ${score} / ${quizData[currentLevel].length}</p>`;
        }

    </script>

</body>
</html>