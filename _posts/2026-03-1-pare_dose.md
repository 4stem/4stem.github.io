---
layout: post
title: "Δώσε Δεδομένα - Πάρε Αποτελέσματα"
description: "Διαδραστική εφαρμογή για ανάλυση πειραματικών δεδομένων Φυσικής"
category: Εφαρμογή
tags: [Εργαστήριο]

---

# Εφαρμογή Ανάλυσης Πειραματικών Δεδομένων

Διαδραστική εφαρμογή για την ανάλυση δεδομένων από πειράματα Φυσικής με υποστήριξη γραμμικής προσαρμογής και μετασχηματισμού X².

## Χαρακτηριστικά

- ✅ Εισαγωγή ζευγαριών δεδομένων με υποστήριξη επιστημονικής σημειογραφίας (π.χ. 1.6e-19)
- ✅ Γραφικές παραστάσεις με άξονες και θετική φορά (→)
- ✅ Γραμμική προσαρμογή με τη μέθοδο ελαχίστων τετραγώνων
- ✅ Αυτόματος μετασχηματισμός σε X² για μη γραμμικές σχέσεις
- ✅ Εμφάνιση αποτελεσμάτων με LaTeX
- ✅ Λειτουργία πλήρους οθόνης
- ✅ Responsive design για όλες τις συσκευές

---

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
    #physics-app-container * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    #physics-app-container {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        min-height: 100vh;
        padding: 20px;
        overflow-x: hidden;
        margin: -20px;
    }

    #physics-app-container .app-container {
        max-width: 900px;
        margin: 0 auto;
        background: white;
        border-radius: 20px;
        box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        padding: 40px;
    }

    #physics-app-container h1.app-title {
        color: #667eea;
        text-align: center;
        margin-bottom: 30px;
        font-size: 2em;
    }

    #physics-app-container .step {
        display: none;
    }

    #physics-app-container .step.active {
        display: block;
        animation: fadeIn 0.5s;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }

    #physics-app-container .form-group {
        margin-bottom: 20px;
    }

    #physics-app-container label {
        display: block;
        margin-bottom: 8px;
        color: #333;
        font-weight: 600;
    }

    #physics-app-container input[type="number"],
    #physics-app-container input[type="text"] {
        width: 100%;
        padding: 12px;
        border: 2px solid #e0e0e0;
        border-radius: 8px;
        font-size: 16px;
        transition: border-color 0.3s;
    }

    #physics-app-container input[type="number"]:focus,
    #physics-app-container input[type="text"]:focus {
        outline: none;
        border-color: #667eea;
    }

    #physics-app-container button {
        background: #667eea;
        color: white;
        border: none;
        padding: 12px 30px;
        border-radius: 8px;
        font-size: 16px;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s;
        margin-right: 10px;
    }

    #physics-app-container button:hover {
        background: #5568d3;
        transform: translateY(-2px);
        box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
    }

    #physics-app-container button.secondary {
        background: #95a5a6;
    }

    #physics-app-container button.secondary:hover {
        background: #7f8c8d;
    }

    #physics-app-container button.danger {
        background: #e74c3c;
    }

    #physics-app-container button.danger:hover {
        background: #c0392b;
    }

    #physics-app-container button.success {
        background: #27ae60;
    }

    #physics-app-container button.success:hover {
        background: #229954;
    }

    #physics-app-container table {
        width: 100%;
        border-collapse: collapse;
        margin: 20px 0;
    }

    #physics-app-container th, #physics-app-container td {
        padding: 12px;
        border: 1px solid #ddd;
        text-align: center;
    }

    #physics-app-container th {
        background: #667eea;
        color: white;
        font-weight: 600;
    }

    #physics-app-container td input {
        width: 100%;
        padding: 8px;
        border: 1px solid #ddd;
        border-radius: 4px;
        text-align: center;
    }

    #physics-app-container .chart-container {
        position: relative;
        height: 400px;
        margin: 30px 0;
    }

    #physics-app-container .result-box {
        background: #f8f9fa;
        border-left: 4px solid #667eea;
        padding: 20px;
        margin: 20px 0;
        border-radius: 8px;
    }

    #physics-app-container .result-box h3 {
        color: #667eea;
        margin-bottom: 10px;
    }

    #physics-app-container .result-box p {
        font-size: 18px;
        color: #333;
        margin: 5px 0;
    }

    #physics-app-container .button-group {
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
        margin-top: 20px;
    }

    #physics-app-container .question-box {
        background: #fff3cd;
        border: 2px solid #ffc107;
        padding: 20px;
        margin: 20px 0;
        border-radius: 8px;
        text-align: center;
    }

    #physics-app-container .question-box h3 {
        color: #856404;
        margin-bottom: 15px;
    }

    #physics-app-container .info-box {
        background: #d1ecf1;
        border: 2px solid #0c5460;
        padding: 15px;
        margin: 15px 0;
        border-radius: 8px;
        color: #0c5460;
    }

    #physics-app-container .fullscreen-btn {
        position: fixed;
        top: 20px;
        right: 20px;
        background: rgba(102, 126, 234, 0.9);
        color: white;
        border: none;
        width: 50px;
        height: 50px;
        border-radius: 50%;
        cursor: pointer;
        font-size: 20px;
        box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        z-index: 1000;
        transition: all 0.3s;
    }

    #physics-app-container .fullscreen-btn:hover {
        background: rgba(85, 104, 211, 1);
        transform: scale(1.1);
    }

    #physics-app-container .social-buttons {
        position: fixed;
        bottom: 30px;
        right: 30px;
        display: flex;
        flex-direction: column;
        gap: 15px;
        z-index: 1000;
    }

    #physics-app-container .social-btn {
        width: 50px;
        height: 50px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        text-decoration: none;
        font-size: 24px;
        box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        transition: all 0.3s;
        cursor: pointer;
    }

    #physics-app-container .social-btn:hover {
        transform: translateY(-5px) scale(1.1);
        box-shadow: 0 8px 25px rgba(0,0,0,0.4);
    }

    #physics-app-container .social-btn.github {
        background: #333;
    }

    #physics-app-container .social-btn.facebook {
        background: #3b5998;
    }

    #physics-app-container .social-btn.twitter {
        background: #1DA1F2;
    }

    #physics-app-container .social-btn.linkedin {
        background: #0077B5;
    }

    #physics-app-container .social-btn.youtube {
        background: #FF0000;
    }

    #physics-app-container .social-btn.wordpress {
        background: #21759B;
    }

    #physics-app-container .social-btn.tumblr {
        background: #35465C;
    }

    body.fullscreen-mode #physics-app-container {
        margin: 0;
        padding: 0;
    }

    body.fullscreen-mode #physics-app-container .app-container {
        max-width: 100%;
        height: 100vh;
        border-radius: 0;
        overflow-y: auto;
    }

    @media (max-width: 600px) {
        #physics-app-container .app-container {
            padding: 20px;
        }

        #physics-app-container h1.app-title {
            font-size: 1.5em;
        }

        #physics-app-container .button-group {
            flex-direction: column;
        }

        #physics-app-container button {
            width: 100%;
            margin-right: 0;
            margin-bottom: 10px;
        }

        #physics-app-container .social-buttons {
            bottom: 20px;
            right: 20px;
            gap: 10px;
        }

        #physics-app-container .social-btn {
            width: 45px;
            height: 45px;
            font-size: 20px;
        }

        #physics-app-container .fullscreen-btn {
            top: 10px;
            right: 10px;
            width: 45px;
            height: 45px;
        }
    }
</style>

<div id="physics-app-container">
    <button class="fullscreen-btn" onclick="toggleFullscreenApp()" title="Πλήρης Οθόνη">
        <i class="fas fa-expand"></i>
    </button>

    <div class="social-buttons">
        <a href="https://github.com/panagiotis2011" target="_blank" class="social-btn github" title="GitHub - Panagiotis Petridis">
            <i class="fab fa-github"></i>
        </a>
        <a href="https://www.facebook.com/papetridis" target="_blank" class="social-btn facebook" title="Facebook - Panagiotis Petridis">
            <i class="fab fa-facebook-f"></i>
        </a>
        <a href="https://www.twitter.com/Petridis_P" target="_blank" class="social-btn twitter" title="Twitter - @Petridis_P">
            <i class="fab fa-twitter"></i>
        </a>
        <a href="http://www.linkedin.com/pub/panagiotis-petridis/42/840/516" target="_blank" class="social-btn linkedin" title="LinkedIn - Panagiotis Petridis">
            <i class="fab fa-linkedin-in"></i>
        </a>
        <a href="https://www.youtube.com/channel/UC0nvnxsK6_cBOFiM19tG0TA" target="_blank" class="social-btn youtube" title="YouTube Channel">
            <i class="fab fa-youtube"></i>
        </a>
        <a href="http://petridis.wordpress.com/" target="_blank" class="social-btn wordpress" title="WordPress Blog">
            <i class="fab fa-wordpress"></i>
        </a>
        <a href="http://28lykeio.tumblr.com/" target="_blank" class="social-btn tumblr" title="28ο Λύκειο - Tumblr">
            <i class="fab fa-tumblr"></i>
        </a>
    </div>

    <div class="app-container">
        <h1 class="app-title">📊 Δώσε Δεδομένα - Πάρε Αποτελέσματα</h1>

        <div id="step1" class="step active">
            <div class="form-group">
                <label for="numPairs">Πόσα ζευγάρια τιμών θα εισάγετε;</label>
                <input type="number" id="numPairs" min="2" placeholder="π.χ. 5">
            </div>
            <button onclick="goToStep2()">Επόμενο →</button>
        </div>

        <div id="step2" class="step">
            <div class="form-group">
                <label for="xLabel">Φυσικό μέγεθος άξονα X:</label>
                <input type="text" id="xLabel" placeholder="π.χ. Χρόνος">
            </div>
            <div class="form-group">
                <label for="xUnit">Μονάδα μέτρησης άξονα X:</label>
                <input type="text" id="xUnit" placeholder="π.χ. s">
            </div>
            <div class="form-group">
                <label for="yLabel">Φυσικό μέγεθος άξονα Y:</label>
                <input type="text" id="yLabel" placeholder="π.χ. Απόσταση">
            </div>
            <div class="form-group">
                <label for="yUnit">Μονάδα μέτρησης άξονα Y:</label>
                <input type="text" id="yUnit" placeholder="π.χ. m">
            </div>
            <div class="button-group">
                <button class="secondary" onclick="goToStep1()">← Πίσω</button>
                <button onclick="goToStep3()">Επόμενο →</button>
            </div>
        </div>

        <div id="step3" class="step">
            <h3>Εισαγωγή Δεδομένων</h3>
            <div class="info-box">
                <strong>💡 Συμβουλή:</strong> Για δυνάμεις του 10, χρησιμοποιήστε: 
                <code>1.6e-19</code> για 1.6×10⁻¹⁹
            </div>
            <div id="dataTable"></div>
            <div class="button-group">
                <button class="secondary" onclick="goToStep2()">← Πίσω</button>
                <button onclick="goToStep4()">Επαλήθευση →</button>
            </div>
        </div>

        <div id="step4" class="step">
            <h3>Επαλήθευση Δεδομένων</h3>
            <div id="verificationTable"></div>
            <div class="button-group">
                <button class="danger" onclick="restartApp()">❌ Λάθος - Ξεκίνα από την αρχή</button>
                <button onclick="goToStep5()">✓ Σωστά - Συνέχεια</button>
            </div>
        </div>

        <div id="step5" class="step">
            <h3>Γραφική Παράσταση</h3>
            <div class="chart-container">
                <canvas id="myChart"></canvas>
            </div>
            <div class="question-box">
                <h3>🤔 Είναι η σχέση γραμμική;</h3>
                <div class="button-group" style="justify-content: center;">
                    <button class="success" onclick="answerLinear(true)">✓ Ναι</button>
                    <button class="danger" onclick="answerLinear(false)">✗ Όχι - Δοκίμασε X²</button>
                </div>
            </div>
        </div>

        <div id="step5b" class="step">
            <h3>Μετασχηματισμός σε X²</h3>
            <div class="info-box">
                <strong>ℹ️ Πληροφορία:</strong> Δημιουργήθηκε νέα στήλη με τα δεδομένα X².
            </div>
            <div id="squaredDataTable"></div>
            <div class="button-group">
                <button class="secondary" onclick="goToStep5()">← Πίσω</button>
                <button onclick="goToStep5c()">Προβολή Γραφήματος →</button>
            </div>
        </div>

        <div id="step5c" class="step">
            <h3>Γραφική Παράσταση με X²</h3>
            <div class="chart-container">
                <canvas id="squaredChart"></canvas>
            </div>
            <div class="question-box">
                <h3>📈 Να σχεδιαστεί η ευθεία;</h3>
                <div class="button-group" style="justify-content: center;">
                    <button class="success" onclick="drawSquaredLine()">✓ Ναι</button>
                    <button class="danger" onclick="restartApp()">✗ Όχι - Ξανά από την αρχή</button>
                </div>
            </div>
        </div>

        <div id="step6" class="step">
            <h3>Γραφική Παράσταση με Ευθεία Προσαρμογής</h3>
            <div class="chart-container">
                <canvas id="finalChart"></canvas>
            </div>
            <div id="slopeResult" class="result-box"></div>
            <div class="button-group">
                <button class="secondary" onclick="restartApp()">🔄 Νέα Ανάλυση</button>
            </div>
        </div>
    </div>
</div>

<script>
    let numPairs, xLabel, xUnit, yLabel, yUnit, dataPoints = [];
    let chart, finalChart, squaredChart;
    let isSquaredMode = false;

    function toggleFullscreenApp() {
        const elem = document.documentElement;
        const btn = document.querySelector('#physics-app-container .fullscreen-btn i');
        
        if (!document.fullscreenElement) {
            elem.requestFullscreen().then(() => {
                document.body.classList.add('fullscreen-mode');
                btn.classList.remove('fa-expand');
                btn.classList.add('fa-compress');
            }).catch(err => {
                alert('Σφάλμα πλήρους οθόνης: ' + err.message);
            });
        } else {
            document.exitFullscreen();
            document.body.classList.remove('fullscreen-mode');
            btn.classList.remove('fa-compress');
            btn.classList.add('fa-expand');
        }
    }

    function formatScientific(value) {
        const absValue = Math.abs(value);
        if (absValue === 0) return '0';
        if (absValue >= 0.01 && absValue < 10000) return value.toFixed(4);
        
        const exponent = Math.floor(Math.log10(absValue));
        const mantissa = value / Math.pow(10, exponent);
        return `\\(${mantissa.toFixed(2)} \\times 10^{${exponent}}\\)`;
    }

    function goToStep1() {
        isSquaredMode = false;
        showStep('step1');
    }

    function goToStep2() {
        numPairs = parseInt(document.getElementById('numPairs').value);
        if (!numPairs || numPairs < 2) {
            alert('Παρακαλώ εισάγετε έγκυρο αριθμό ζευγαριών (τουλάχιστον 2)');
            return;
        }
        showStep('step2');
    }

    function goToStep3() {
        xLabel = document.getElementById('xLabel').value;
        xUnit = document.getElementById('xUnit').value;
        yLabel = document.getElementById('yLabel').value;
        yUnit = document.getElementById('yUnit').value;

        if (!xLabel || !xUnit || !yLabel || !yUnit) {
            alert('Παρακαλώ συμπληρώστε όλα τα πεδία');
            return;
        }

        createDataTable();
        showStep('step3');
    }

    function createDataTable() {
        let tableHTML = '<table><thead><tr>';
        tableHTML += `<th>${xLabel} (${xUnit})</th>`;
        tableHTML += `<th>${yLabel} (${yUnit})</th>`;
        tableHTML += '</tr></thead><tbody>';

        for (let i = 0; i < numPairs; i++) {
            tableHTML += '<tr>';
            tableHTML += `<td><input type="number" step="any" id="x${i}" placeholder="π.χ. 1.6e-19"></td>`;
            tableHTML += `<td><input type="number" step="any" id="y${i}" placeholder="Τιμή Y"></td>`;
            tableHTML += '</tr>';
        }

        tableHTML += '</tbody></table>';
        document.getElementById('dataTable').innerHTML = tableHTML;
    }

    function goToStep4() {
        dataPoints = [];
        for (let i = 0; i < numPairs; i++) {
            const x = parseFloat(document.getElementById(`x${i}`).value);
            const y = parseFloat(document.getElementById(`y${i}`).value);

            if (isNaN(x) || isNaN(y)) {
                alert('Παρακαλώ συμπληρώστε όλες τις τιμές');
                return;
            }

            dataPoints.push({ x, y });
        }

        createVerificationTable();
        showStep('step4');
    }

    function createVerificationTable() {
        let tableHTML = '<table><thead><tr>';
        tableHTML += `<th>${xLabel} (${xUnit})</th>`;
        tableHTML += `<th>${yLabel} (${yUnit})</th>`;
        tableHTML += '</tr></thead><tbody>';

        dataPoints.forEach(point => {
            tableHTML += `<tr><td>${formatScientific(point.x)}</td><td>${formatScientific(point.y)}</td></tr>`;
        });

        tableHTML += '</tbody></table>';
        document.getElementById('verificationTable').innerHTML = tableHTML;
        
        if (window.MathJax) {
            MathJax.typesetPromise();
        }
    }

    function goToStep5() {
        createChart();
        showStep('step5');
    }

    function createChart() {
        const ctx = document.getElementById('myChart');
        if (chart) chart.destroy();

        chart = new Chart(ctx, {
            type: 'scatter',
            data: {
                datasets: [{
                    label: 'Μετρήσεις',
                    data: dataPoints,
                    backgroundColor: '#e74c3c',
                    borderColor: '#c0392b',
                    pointRadius: 8,
                    pointHoverRadius: 10
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        title: {
                            display: true,
                            text: `${xLabel} (${xUnit}) →`,
                            font: { size: 16, weight: 'bold' }
                        },
                        ticks: {
                            callback: function(value) {
                                return value.toExponential(2);
                            }
                        }
                    },
                    y: {
                        title: {
                            display: true,
                            text: `${yLabel} (${yUnit}) →`,
                            font: { size: 16, weight: 'bold' }
                        },
                        ticks: {
                            callback: function(value) {
                                return value.toExponential(2);
                            }
                        }
                    }
                },
                plugins: {
                    legend: {
                        display: true,
                        position: 'top'
                    }
                }
            }
        });
    }

    function answerLinear(isLinear) {
        if (isLinear) {
            isSquaredMode = false;
            calculateLinearRegression(dataPoints, false);
            showStep('step6');
        } else {
            isSquaredMode = true;
            createSquaredDataTable();
            showStep('step5b');
        }
    }

    function createSquaredDataTable() {
        let tableHTML = '<table><thead><tr>';
        tableHTML += `<th>${xLabel} (${xUnit})</th>`;
        tableHTML += `<th>${xLabel}² (${xUnit}²)</th>`;
        tableHTML += `<th>${yLabel} (${yUnit})</th>`;
        tableHTML += '</tr></thead><tbody>';

        dataPoints.forEach(point => {
            const x2 = point.x * point.x;
            tableHTML += `<tr>`;
            tableHTML += `<td>${formatScientific(point.x)}</td>`;
            tableHTML += `<td>${formatScientific(x2)}</td>`;
            tableHTML += `<td>${formatScientific(point.y)}</td>`;
            tableHTML += `</tr>`;
        });

        tableHTML += '</tbody></table>';
        document.getElementById('squaredDataTable').innerHTML = tableHTML;
        
        if (window.MathJax) {
            MathJax.typesetPromise();
        }
    }

    function goToStep5c() {
        createSquaredChart();
        showStep('step5c');
    }

    function createSquaredChart() {
        const ctx = document.getElementById('squaredChart');
        if (squaredChart) squaredChart.destroy();

        const squaredPoints = dataPoints.map(p => ({ x: p.x * p.x, y: p.y }));

        squaredChart = new Chart(ctx, {
            type: 'scatter',
            data: {
                datasets: [{
                    label: 'Μετρήσεις (X²)',
                    data: squaredPoints,
                    backgroundColor: '#e74c3c',
                    borderColor: '#c0392b',
                    pointRadius: 8,
                    pointHoverRadius: 10
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        title: {
                            display: true,
                            text: `${xLabel}² (${xUnit}²) →`,
                            font: { size: 16, weight: 'bold' }
                        },
                        ticks: {
                            callback: function(value) {
                                return value.toExponential(2);
                            }
                        }
                    },
                    y: {
                        title: {
                            display: true,
                            text: `${yLabel} (${yUnit}) →`,
                            font: { size: 16, weight: 'bold' }
                        },
                        ticks: {
                            callback: function(value) {
                                return value.toExponential(2);
                            }
                        }
                    }
                },
                plugins: {
                    legend: {
                        display: true,
                        position: 'top'
                    }
                }
            }
        });
    }

    function drawSquaredLine() {
        const squaredPoints = dataPoints.map(p => ({ x: p.x * p.x, y: p.y }));
        calculateLinearRegression(squaredPoints, true);
        showStep('step6');
    }

    function calculateLinearRegression(points, isSquared) {
        const n = points.length;
        let sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0;

        points.forEach(point => {
            sumX += point.x;
            sumY += point.y;
            sumXY += point.x * point.y;
            sumX2 += point.x * point.x;
        });

        const slope = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
        const intercept = (sumY - slope * sumX) / n;

        const minX = Math.min(...points.map(p => p.x));
        const maxX = Math.max(...points.map(p => p.x));

        const linePoints = [
            { x: minX, y: slope * minX + intercept },
            { x: maxX, y: slope * maxX + intercept }
        ];

        createFinalChart(points, linePoints, slope, intercept, isSquared);
    }

    function createFinalChart(points, linePoints, slope, intercept, isSquared) {
        const ctx = document.getElementById('finalChart');
        if (finalChart) finalChart.destroy();

        const xAxisLabel = isSquared ? `${xLabel}² (${xUnit}²) →` : `${xLabel} (${xUnit}) →`;
        const xAxisUnit = isSquared ? `${xUnit}²` : xUnit;

        finalChart = new Chart(ctx, {
            type: 'scatter',
            data: {
                datasets: [
                    {
                        label: 'Μετρήσεις',
                        data: points,
                        backgroundColor: '#e74c3c',
                        borderColor: '#c0392b',
                        pointRadius: 8,
                        pointHoverRadius: 10,
                        showLine: false
                    },
                    {
                        label: 'Ευθεία Προσαρμογής',
                        data: linePoints,
                        type: 'line',
                        borderColor: '#3498db',
                        backgroundColor: 'rgba(52, 152, 219, 0.1)',
                        borderWidth: 3,
                        pointRadius: 0,
                        fill: false
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        title: {
                            display: true,
                            text: xAxisLabel,
                            font: { size: 16, weight: 'bold' }
                        },
                        ticks: {
                            callback: function(value) {
                                return value.toExponential(2);
                            }
                        }
                    },
                    y: {
                        title: {
                            display: true,
                            text: `${yLabel} (${yUnit}) →`,
                            font: { size: 16, weight: 'bold' }
                        },
                        ticks: {
                            callback: function(value) {
                                return value.toExponential(2);
                            }
                        }
                    }
                },
                plugins: {
                    legend: {
                        display: true,
                        position: 'top'
                    }
                }
            }
        });

        document.getElementById('slopeResult').innerHTML = `
            <h3>📈 Αποτελέσματα Γραμμικής Προσαρμογής</h3>
            <p><strong>Κλίση (Εφαπτομένη):</strong> ${formatScientific(slope)} ${yUnit}/${xAxisUnit}</p>
            <p><strong>Σταθερά (y-intercept):</strong> ${formatScientific(intercept)} ${yUnit}</p>
            <p><strong>Εξίσωση Ευθείας:</strong> y = ${formatScientific(slope)}x + ${formatScientific(intercept)}</p>
        `;
        
        if (window.MathJax) {
            MathJax.typesetPromise();
        }
    }

    function showStep(stepId) {
        document.querySelectorAll('#physics-app-container .step').forEach(step => {
            step.classList.remove('active');
        });
        document.getElementById(stepId).classList.add('active');
    }

    function restartApp() {
        if (confirm('Θέλετε να ξεκινήσετε από την αρχή;')) {
            dataPoints = [];
            isSquaredMode = false;
            if (chart) chart.destroy();
            if (finalChart) finalChart.destroy();
            if (squaredChart) squaredChart.destroy();
            
            document.getElementById('numPairs').value = '';
            document.getElementById('xLabel').value = '';
            document.getElementById('xUnit').value = '';
            document.getElementById('yLabel').value = '';
            document.getElementById('yUnit').value = '';
            
            showStep('step1');
        }
    }
</script>



## 📖 Οδηγίες  χρήσης

### Τρόπος 1: Χρήση Online (Απλούστερο)

Απλά χρησιμοποιήστε την εφαρμογή πάνω σε αυτή τη σελίδα! Δεν χρειάζεται να κατεβάσετε τίποτα.

### Τρόπος 2: Κατέβασμα και Χρήση Offline

#### Βήμα 1: Κατέβασμα

## 💾 Λήψη από Google Drive

[📥 Κατέβασμα Εφαρμογής](https://drive.google.com/uc?export=download&id=1gG5bR42wTInPXK2EDc0KqSmkVVoAAXCb)


**Σημαντικό για Windows:**
- Αν ο browser σας ρωτήσει "Keep" ή "Discard", πατήστε **Keep**
- Αν εμφανιστεί προειδοποίηση ασφαλείας, πατήστε **Keep anyway** (το αρχείο είναι αρχείο html 100% ασφαλές)

#### Βήμα 2: Αποθήκευση

Το αρχείο θα αποθηκευτεί στον φάκελο **Downloads** (Λήψεις) του υπολογιστή σας με το όνομα `pare_dose.html`

#### Βήμα 3: Άνοιγμα

**Για Windows/Mac/Linux:**
- Βρείτε το αρχείο στον φάκελο Λήψεις
- Κάντε **διπλό κλικ** πάνω του
- Θα ανοίξει αυτόματα στον browser σας (Chrome, Firefox, Safari, Edge)

**Εναλλακτικά:**
- Δεξί κλικ στο αρχείο → **Open with** → Επιλέξτε τον browser σας

#### Βήμα 4: Χρήση

Τώρα μπορείτε να χρησιμοποιήσετε την εφαρμογή όποτε θέλετε, ακόμα και χωρίς Internet!

**💡 Συμβουλή:** Αντιγράψτε το αρχείο στην Επιφάνεια Εργασίας για πιο εύκολη πρόσβαση.

---

### Αντιμετώπιση Προβλημάτων

#### ❓ Το αρχείο δεν ανοίγει

**Λύση 1:**
- Δεξί κλικ στο αρχείο
- **Open with** → Επιλέξτε **Google Chrome** (ή Firefox, Edge)

**Λύση 2:**
- Ανοίξτε τον browser σας
- Πατήστε **Ctrl+O** (Windows) ή **Cmd+O** (Mac)
- Βρείτε και επιλέξτε το αρχείο

#### ❓ Εμφανίζεται σαν κείμενο αντί για εφαρμογή

Αυτό σημαίνει ότι άνοιξε με Notepad/TextEdit αντί για browser.
- Δεξί κλικ → **Open with** → **Browser** (Chrome, Firefox, etc.)

#### ❓ Τα μαθηματικά σύμβολα δεν φαίνονται σωστά

Χρειάζεται Internet την πρώτη φορά για να φορτώσει το MathJax.
Μετά από αυτό, θα δουλεύει και offline.

#### ❓ Τα γραφήματα δεν εμφανίζονται

Όπως παραπάνω - χρειάζεται Internet την πρώτη χρήση για Chart.js.

---

### 📱 Χρήση σε Κινητό/Tablet

Η εφαρμογή λειτουργεί και σε κινητές συσκευές!

**Android:**
1. Κατεβάστε το αρχείο
2. Ανοίξτε το με Chrome ή Firefox
3. Προσθέστε στην αρχική οθόνη για γρήγορη πρόσβαση

**iOS (iPhone/iPad):**
1. Κατεβάστε το αρχείο
2. Ανοίξτε το με Safari
3. Πατήστε το εικονίδιο κοινοποίησης → **Add to Home Screen**

---

### 🎯 Tips για Καλύτερη Εμπειρία

1. **Πλήρης Οθόνη**: Πατήστε το κουμπί ⛶ πάνω δεξιά για fullscreen mode
2. **Αποθήκευση Δεδομένων**: Προς το παρόν η εφαρμογή δεν αποθηκεύει δεδομένα. Σημειώστε τα αποτελέσματά σας!
3. **Screenshots**: Χρησιμοποιήστε το Print Screen για να αποθηκεύσετε τις γραφικές παραστάσεις

---

### 🆘 Χρειάζεστε Βοήθεια;

Αν έχετε πρόβλημα, επικοινωνήστε μαζί μου μέσω:
- Email: [sch@sch.gr]
ή στα social media buttons!