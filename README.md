<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Encuesta CCOO de Factores y Síntomas de Estrés Térmico</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: url('https://aragon.fsc.ccoo.es/630a74e7e957c7ffa8bd1e87dc4ba425000050.png'); /* Reemplaza con la URL de tu imagen */
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .content {
            background-color: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            width: 80%;
            max-width: 600px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .result, .symptom-section, .contact-delegates {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ccc;
            display: none;
        }
    </style>
</head>
<body>
    <div class="content">
        <h1>Encuesta de Factores y Síntomas de Estrés Térmico</h1>
        <form id="surveyForm">
            <div class="factor-section">
                <label for="highTemp">¿Consideras que la temperatura en tu área de trabajo es alta?</label><br>
                <input type="radio" id="highTempYes" name="highTemp" value="yes" required>
                <label for="highTempYes">Sí</label><br>
                <input type="radio" id="highTempNo" name="highTemp" value="no" required>
                <label for="highTempNo">No</label><br><br>

                <label for="heavyWork">¿Realizas trabajo físico pesado?</label><br>
                <input type="radio" id="heavyWorkYes" name="heavyWork" value="yes" required>
                <label for="heavyWorkYes">Sí</label><br>
                <input type="radio" id="heavyWorkNo" name="heavyWork" value="no" required>
                <label for="heavyWorkNo">No</label><br><br>

                <label for="poorVentilation">¿Tu área de trabajo tiene una ventilación adecuada?</label><br>
                <input type="radio" id="poorVentilationYes" name="poorVentilation" value="yes" required>
                <label for="poorVentilationYes">Sí</label><br>
                <input type="radio" id="poorVentilationNo" name="poorVentilation" value="no" required>
                <label for="poorVentilationNo">No</label><br><br>

                <label for="longExposure">¿Permaneces largas horas expuesto a fuentes de calor?</label><br>
                <input type="radio" id="longExposureYes" name="longExposure" value="yes" required>
                <label for="longExposureYes">Sí</label><br>
                <input type="radio" id="longExposureNo" name="longExposure" value="no" required>
                <label for="longExposureNo">No</label><br><br>
            </div>

            <div class="contact-delegates">
                <p><strong>Contacto:</strong> Se han identificado factores de riesgo de estrés térmico. Por favor, ponte en contacto con delegado/a.</p>
                <button type="button" onclick="showSymptomSection()">Es importante, continua la encuesta</button>
            </div>

            <div class="symptom-section">
                <h2>Preguntas sobre Síntomas</h2>
                <label for="dizziness">¿Sientes mareos o vértigo frecuentemente en el trabajo?</label><br>
                <input type="radio" id="dizzinessYes" name="dizziness" value="yes">
                <label for="dizzinessYes">Sí</label><br>
                <input type="radio" id="dizzinessNo" name="dizziness" value="no">
                <label for="dizzinessNo">No</label><br><br>

                <label for="fatigue">¿Sientes fatiga extrema o cansancio más allá de lo normal?</label><br>
                <input type="radio" id="fatigueYes" name="fatigue" value="yes">
                <label for="fatigueYes">Sí</label><br>
                <input type="radio" id="fatigueNo" name="fatigue" value="no">
                <label for="fatigueNo">No</label><br><br>

                <label for="excessiveSweating">¿Sudas en exceso mientras trabajas, incluso sin realizar esfuerzo físico significativo?</label><br>
                <input type="radio" id="excessiveSweatingYes" name="excessiveSweating" value="yes">
                <label for="excessiveSweatingYes">Sí</label><br>
                <input type="radio" id="excessiveSweatingNo" name="excessiveSweating" value="no">
                <label for="excessiveSweatingNo">No</label><br><br>

                <label for="nausea">¿Has experimentado náuseas o vómitos mientras trabajas?</label><br>
                <input type="radio" id="nauseaYes" name="nausea" value="yes">
                <label for="nauseaYes">Sí</label><br>
                <input type="radio" id="nauseaNo" name="nausea" value="no">
                <label for="nauseaNo">No</label><br><br>
            </div>

            <button type="button" onclick="checkFactors()">Enviar</button>
        </form>

        <div id="result" class="result"></div>
    </div>

    <script>
        function checkFactors() {
            var highTemp = document.querySelector('input[name="highTemp"]:checked').value;
            var heavyWork = document.querySelector('input[name="heavyWork"]:checked').value;
            var poorVentilation = document.querySelector('input[name="poorVentilation"]:checked').value;
            var longExposure = document.querySelector('input[name="longExposure"]:checked').value;

            var factors = [highTemp, heavyWork, poorVentilation, longExposure];
            var factorCount = factors.filter(factor => factor === 'yes').length;

            if (factorCount >= 2) {
                document.querySelector('.contact-delegates').style.display = 'block';
            } else {
                displayResult(false);
            }
        }

        function showSymptomSection() {
            document.querySelector('.contact-delegates').style.display = 'none';
            document.querySelector('.symptom-section').style.display = 'block';
            document.querySelector('button[onclick="checkFactors()"]').setAttribute('onclick', 'calculateStress()');
        }

        function calculateStress() {
            var dizziness = document.querySelector('input[name="dizziness"]:checked').value;
            var fatigue = document.querySelector('input[name="fatigue"]:checked').value;
            var excessiveSweating = document.querySelector('input[name="excessiveSweating"]:checked').value;
            var nausea = document.querySelector('input[name="nausea"]:checked').value;

            var symptoms = [dizziness, fatigue, excessiveSweating, nausea];
            var symptomCount = symptoms.filter(symptom => symptom === 'yes').length;

            displayResult(symptomCount >= 2);
        }

        function displayResult(isStress) {
            var resultDiv = document.getElementById('result');
            if (isStress) {
                resultDiv.innerHTML = `
                    <strong>Alerta:</strong> Hay indicios de Sock térmico en tu lugar de trabajo.<br><br>
                    <strong>Instrucciones:</strong>
                    <ol>
                        <li>Avisar al 112 y servicios sanitarios.</li>
                        <li>Colocar a la persona afectada en posición horizontal en un lugar fresco y ventilado.</li>
                        <li>Intentar enfriarle la piel, impregnando la misma con compresas mojadas en agua fría, sobre todo en cuello, cabeza, axilas e ingles.</li>
                        <li>Abanicar al afectado para seguir refrescando el resto de piel.</li>
                        <li>Retirarle las prendas no necesarias y mantener libres sus vías respiratorias.</li>
                        <li>No dejarle nunca solo, hasta que llegue la asistencia sanitaria.</li>
                    </ol>
                `;
                resultDiv.style.backgroundColor = "#f8d7da";
                resultDiv.style.color = "#721c24";
                resultDiv.style.borderColor = "#f5c6cb";
            } else {
                resultDiv.innerHTML = "<strong>Bien:</strong> No hay indicios de Estrés-Shock térmico en tu lugar de trabajo.";
                resultDiv.style.backgroundColor = "#d4edda";resultDiv.style.color = "#155724";
                resultDiv.style.borderColor = "#c3e6cb";
            }
            resultDiv.style.display = "block";
        }
    </script>
</body>
</html>
