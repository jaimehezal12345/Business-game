# Business-game
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Decisiones Estratégicas de Apple</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
            max-width: 600px;
            margin: auto;
        }
        .question {
            margin-bottom: 20px;
        }
        .options {
            margin: 10px 0;
        }
        .btn {
            padding: 10px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .btn:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <h1>Decisiones Estratégicas de Apple</h1>
    <div id="game">
        <div id="scenario" class="question">
            <!-- The scenario text will be inserted here -->
        </div>
        <div id="options" class="options">
            <!-- The options buttons will be inserted here -->
        </div>
        <button class="btn" id="nextButton" style="display: none;">Siguiente</button>
        <div id="result" style="display: none;">
            <h2>Resultados</h2>
            <p id="resultText"></p>
        </div>
    </div>

    <script>
        const scenarios = [
            {
                question: "Apple está considerando lanzar un nuevo iPhone. ¿Qué precio debería establecer?",
                options: [
                    { text: "$999", impact: "positive" },
                    { text: "$699", impact: "negative" }
                ]
            },
            {
                question: "Apple planea expandirse a India. ¿Cuál debería ser la estrategia de precios?",
                options: [
                    { text: "Modelo básico a precio bajo", impact: "positive" },
                    { text: "Modelo avanzado a precio alto", impact: "negative" }
                ]
            },
            {
                question: "Apple tiene un presupuesto limitado para publicidad. ¿Qué tipo de campaña deberían elegir?",
                options: [
                    { text: "Campaña digital", impact: "positive" },
                    { text: "Medios tradicionales", impact: "negative" }
                ]
            }
        ];

        let currentScenario = 0;
        let score = 0;

        function displayScenario() {
            const scenario = scenarios[currentScenario];
            document.getElementById('scenario').innerText = scenario.question;
            document.getElementById('options').innerHTML = scenario.options.map((opt, index) => 
                `<button class="btn" onclick="selectOption(${index})">${opt.text}</button>`
            ).join(' ');
            document.getElementById('nextButton').style.display = 'none';
        }

        function selectOption(index) {
            const impact = scenarios[currentScenario].options[index].impact;
            if (impact === "positive") {
                score++;
            }
            currentScenario++;
            if (currentScenario < scenarios.length) {
                document.getElementById('nextButton').style.display = 'block';
            } else {
                showResults();
            }
        }

        function showResults() {
            document.getElementById('game').style.display = 'none';
            document.getElementById('result').style.display = 'block';
            document.getElementById('resultText').innerText = `Tu puntaje final es ${score} de ${scenarios.length}.`;
        }

        document.getElementById('nextButton').addEventListener('click', () => {
            displayScenario();
        });

        // Initialize the game
        displayScenario();
    </script>
</body>
</html>
