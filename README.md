<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CCOO Encuesta de Factores y Síntomas de Estrés Térmico</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: url('https://andalucia.fsc.ccoo.es/cc1014c18d30a73595e4f13557725893000050.jpg'); /* Reemplaza con la URL de tu imagen */
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
            position: relative;
        }
        .result, .instructions, .message {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ccc;
            text-align: center;
            display: none;
        }
        .message {
            background-color: #fff3cd;
            color: #856404;
            border-color: #ffeeba;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 10;
            width: 80%;
            max-width: 500px;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
    </style>
</head>
<body>
    <div id="page1" class="content">
        <h1>CCOO Encuesta de Factores de Estrés Térmico</h1>
        <form id="surveyForm1">
            <label for="highTemp">¿Consideras que la temperatura en tu área de trabajo es alta?</label><br>
            <input type="radio" id="highTempYes" name="highTemp" value="sí" required>
            <label for="highTempYes">Sí</label><br>
            <input type="radio" id="highTempNo" name="highTemp" value="no" required>
            <label for="highTempNo">No</label><br><br>

            <label for="heavyWork">¿Realizas trabajo físico pesado?</label><br>
            <input type="radio" id="heavyWorkYes" name="heavyWork" value="sí" required>
            <label for="heavyWorkYes">Sí</label><br>
            <input type="radio" id="heavyWorkNo" name="heavyWork" value="no" required>
            <label for="heavyWorkNo">No</label><br><br>

            <label for="poorVentilation">¿Tu área de trabajo tiene una ventilación adecuada?</label><br>
            <input type="radio" id="poorVentilationYes" name="poorVentilation" value="sí" required>
            <label for="poorVentilationYes">Sí</label><br>
            <input type="radio" id="poorVentilationNo" name="poorVentilation" value="no" required>
            <label for="poorVentilationNo">No</label><br><br>

            <label for="longExposure">¿Permaneces largas horas expuesto a fuentes de calor?</label><br>
            <input type="radio" id="longExposureYes" name="longExposure" value="sí" required>
            <label for="longExposureYes">Sí</label><br>
            <input type="radio" id="longExposureNo" name="longExposure" value="no" required>
            <label for="longExposureNo">No</label><br><br>

            <button type="button" onclick="checkFactors()">Continuar</button>
        </form>

        <div id="result1" class="result"></div>
        <div id="message1" class="message"></div>
    </div>

    <div id="page2" class="content" style="display: none;">
        <h1>Encuesta de Síntomas de Estrés Térmico</h1>
        <form id="surveyForm2">
            <label for="dizziness">¿Sientes mareos o vértigo frecuentemente en el trabajo?</label><br>
            <input type="radio" id="dizzinessYes" name="dizziness" value="sí">
            <label for="dizzinessYes">Sí</label><br>
            <input type="radio" id="dizzinessNo" name="dizziness" value="no">
            <label for="dizzinessNo">No</label><br><br>

            <label for="fatigue">¿Sientes fatiga extrema o cansancio más allá de lo normal?</label><br>
            <input type="radio" id="fatigueYes" name="fatigue" value="sí">
            <label for="fatigueYes">Sí</label><br>
            <input type="radio" id="fatigueNo" name="fatigue" value="no">
            <label for="fatigueNo">No</label><br><br>

            <label for="excessiveSweating">¿Sudas en exceso mientras trabajas, incluso sin realizar esfuerzo físico significativo?</label><br>
            <input type="radio" id="excessiveSweatingYes" name="excessiveSweating" value="sí">
            <label for="excessiveSweatingYes">Sí</label><br>
            <input type="radio" id="excessiveSweatingNo" name="excessiveSweating" value="no">
            <label for="excessiveSweatingNo">No</label><br><br>

            <label for="nausea">¿Has experimentado náuseas o vómitos mientras trabajas?</label><br>
            <input type="radio" id="nauseaYes" name="nausea" value="sí">
            <label for="nauseaYes">Sí</label><br>
            <input type="radio" id="nauseaNo" name="nausea" value="no">
            <label for="nauseaNo">No</label><br><br>

            <button type="button" onclick="calculateStress()">Enviar</button>
        </form>

        <div id="result2" class="result"></div>
        <div id="message2" class="message"></div>
    </div>

    <div id="instructions" class="content" style="display: none;">
        <h1>CCOO Instrucciones en caso de Shock térmico</h1>
        <ol>
            <li>Avisar al 112 y servicios sanitarios.</li>
            <li>Colocar a la persona afectada en posición horizontal en un lugar fresco y ventilado.</li>
            <li>Intentar enfriarle la piel, impregnando la misma con compresas mojadas en agua fría, sobre todo en cuello, cabeza, axilas e ingles.</li>
            <li>Abanicar al afectado para seguir refrescando el resto de piel.</li>
            <li>Retirarle las prendas no necesarias y mantener libres sus vías respiratorias.</li>
            <li>No dejarle nunca solo, hasta que llegue la asistencia sanitaria.</li>
        </ol>
    </div>

    <script>
        function checkFactors() {
            var highTemp = document.querySelector('input[name="highTemp"]:checked').value;
            var heavyWork = document.querySelector('input[name="heavyWork"]:checked').value;
            var poorVentilation = document.querySelector('input[name="poorVentilation"]:checked').value;
            var longExposure = document.querySelector('input[name="longExposure"]:checked').value;

            var factors = [highTemp, heavyWork, poorVentilation, longExposure];
            var factorCount = factors.filter(factor => factor === 'sí').length;

            var messageDiv = document.getElementById('message1');
            if (factorCount >= 2) {
                messageDiv.innerHTML = "Hay factores de riesgo por estrés-shock térmico. Por favor, ponte en contacto con tus delegados y sigue Respondiendo.";
                messageDiv.style.display = "block";
                setTimeout(() => {
                    showPage2();
                }, 5000);
            } else {
                displayResult(false, 1);
            }
        }

        function showPage2() {
            document.getElementById('page1').style.display = 'none';
            document.getElementById('page2').style.display = 'block';
        }

        function calculateStress() {
            var dizziness = document.querySelector('input[name="dizziness"]:checked').value;
            var fatigue = document.querySelector('input[name="fatigue"]:checked').value;
            var excessiveSweating = document.querySelector('input[name="excessiveSweating"]:checked').value;
            var nausea = document.querynausea = document.querySelector('input[name="nausea"]:checked').value;

            var symptoms = [dizziness, fatigue, excessiveSweating, nausea];
            var symptomCount = symptoms.filter(symptom => symptom === 'sí').length;

            var messageDiv = document.getElementById('message2');
            if (symptomCount >= 2) {
                messageDiv.innerHTML = "Alerta: Hay indicios de estrés-shock térmico en tu lugar de trabajo.";
                messageDiv.style.display = "block";
                setTimeout(() => {
                    showInstructions();
                }, 5000);
            } else {
                displayResult(false, 2);
            }
        }

        function showInstructions() {
            document.getElementById('page2').style.display = 'none';
            document.getElementById('instructions').style.display = 'block';
        }

        function displayResult(isStress, page) {
            var resultDiv = document.getElementById('result' + page);
            if (isStress) {
                resultDiv.innerHTML = `
                    <strong>Alerta:</strong> Hay indicios de shock térmico en tu lugar de trabajo.<br><br>
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
                document.getElementById('instructions').style.display = 'block';
            } else {
                resultDiv.innerHTML = "<strong>Bien:</strong> No hay indicios de estrés térmico en tu lugar de trabajo.";
                resultDiv.style.backgroundColor = "#d4edda";
                resultDiv.style.color = "#155724";
                resultDiv.style.borderColor = "#c3e6cb";
            }
            resultDiv.style.display = "block";
        }
    </script>
</body>
</html>
