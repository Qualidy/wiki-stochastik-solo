<html><head><base href="." /><meta http-equiv="content-type" content="text/html; charset=utf-8">
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
document.addEventListener('DOMContentLoaded', function() { 
    let variances = [];
    let variancesSchaetzer = [];
    let chart;
    let popChart;
    

    function getButtons() {
        return document.querySelectorAll('.sample-button');
    }   

    function buttonsDisabled(disabled) {
        getButtons().forEach(btn => btn.disabled = disabled)
    }

    function getCheckboxes(){
        return document.querySelectorAll('.sample-checkbox');
    }

    function getValueInputs() {
        return document.querySelectorAll('.value-input');
    }

    function getNumberOfAllValues(){
        return getValueInputs().length;
    }

    function getSampleButtons(){
        return document.querySelectorAll('.sample-button');
    }

    function getAllInputs() {
        const valueInputs = getValueInputs();
        return Array.from(valueInputs).map(input => parseFloat(input.value));
    }

    function getSelectedInputs(){
        const checkboxes = getCheckboxes();
        return getAllInputs().filter((_, index) => checkboxes[index].checked);
    }

    function mean(values) {
        return values.reduce((a, b) => a + b, 0) / values.length;
    }

    function variance(values, ddof=0) {
        const m = mean(values)
        return values.reduce((acc, val) => acc + Math.pow(val - m, 2), 0) / (values.length - ddof);
    }

    function std(values, ddof=0){
        return Math.sqrt(variance(values, ddof));
    }

    function insertRandomValues0(){
        const valueInputs = getValueInputs();
        valueInputs.forEach(input => {
            input.value = Math.floor(100 + Math.random() * 1000);
        });
    }
    
    function generateNormalRandom(mean = 100, stddev = 15) {
        let u1 = Math.random();
        let u2 = Math.random();
        let z0 = Math.sqrt(-2.0 * Math.log(u1)) * Math.cos(2.0 * Math.PI * u2);
        return z0 * stddev + mean;
    }
    
    function insertRandomValues() {
        const valueInputs = getValueInputs();
        valueInputs.forEach(input => {
            // Generiert einen Wert aus einer Normalverteilung mit Mittelwert und Standardabweichung
            input.value = Math.round(generateNormalRandom(100, 50));
        });
    }

    function generateRandomBooleans(length, p = 0.5) {
        return Array.from({ length }, () => Math.random() < p);
    }

    function initilizeButtons() {
        getSampleButtons().forEach(button => {
            button.addEventListener('click', () => {
                generateSamples(parseInt(button.dataset.samples), parseInt(button.dataset.delay), button);
            });
        });
    }

    async function generateSamples(count, delay, button) {
        buttonsDisabled(true)

        for (let i = 0; i < count; i++) {
            button.style.background = `linear-gradient(to right, #4CAF50 ${(i/count)*100}%, #a0d3a1 ${(i/count)*100}%)`;
            generateSample();
            variances.push(getSampleStd());
            variancesSchaetzer.push(getSchaetzerStd());
            updateResults();
            updateVarianceChart();
            await new Promise(resolve => setTimeout(resolve, delay));
        }
        button.style.background = '';
        buttonsDisabled(false)
    }
    
    function generateSample() {
        const checkboxes = getCheckboxes();
        
        let randomBooleans = [];
        do {
            randomBooleans = generateRandomBooleans(checkboxes.length);
        } while (randomBooleans.filter(Boolean).length < 2 || randomBooleans.filter(Boolean).length > randomBooleans.length);

        checkboxes.forEach((checkbox, index) => {
            checkbox.checked = randomBooleans[index];
        });
    }

    function initilizePopulationChart(){
        const ctx = document.getElementById('populationChart');
        popChart = new Chart(ctx, {
            type: 'scatter',
            data: {
                datasets: [{
                    label: 'Datapoints',
                    data: list_to_data(getAllInputs()),
                    backgroundColor: 'rgba(54, 162, 235, 0.5)'
                },{
                    label: 'Selected Datepoints',
                },{
                },{
                },{
                },{
                },{
                },{
                    label: 'Mittelwert',
                    data: [],
                    backgroundColor: 'rgba(54, 55, 100, 0.5)', 
                    borderWidth: 2,
                    type: 'line'
                }]
            },
            options: {
                scales: {
                    y: {
                        beginAtZero: true
                    }
                },
                animation: {
                    duration: 0
                }
            }
        });
        popChart.update();
    }

    function initilizeVarianceChart(){
        const ctx = document.getElementById('varianceChart');
        chart = new Chart(ctx, {
            type: 'scatter',
            data: {
                datasets: [{
                    label: 'Sample Standard Deviations',
                    data: variances,
                    backgroundColor: 'rgba(54, 162, 235, 0.5)'
                },{
                    label: 'Schätzer Standard Deviations',
                    data: variancesSchaetzer,
                    backgroundColor: 'rgba(54, 55, 100, 0.5)'
                },{
                    label: 'Population Standard Deviation',
                    data: [],
                    borderColor: 'rgba(255, 99, 132, 1)',
                    borderWidth: 2,
                    type: 'line'
                }, {
                    label: 'Average Sample Standard Deviation',
                    data: [],
                    borderColor: 'rgba(75, 192, 192, 1)',
                    borderWidth: 2,
                    type: 'line'
                }, {
                    label: 'Average Schätzer Standard Deviation',
                    data: [],
                    borderColor: 'rgba(12, 192, 22, 1)',
                    borderWidth: 2,
                    type: 'line'
                }]
            },
            options: {
                scales: {
                    y: {
                        beginAtZero: true
                    }
                },
                animation: {
                    duration: 0
                },
            plugins: {
            // Zeichnet die horizontale Linie
            beforeDraw: function(chart) {
                const yValue = 70; // Der y-Wert für die Linie
                const yScale = chart.scales['y'];
                const yPixel = yScale.getPixelForValue(yValue);

                const ctx = chart.ctx;
                ctx.save();
                ctx.strokeStyle = 'red';
                ctx.lineWidth = 2;
                ctx.beginPath();
                ctx.moveTo(chart.chartArea.left, yPixel);
                ctx.lineTo(chart.chartArea.right, yPixel);
                ctx.stroke();
                ctx.restore();
            }
        }
            }
        });

    }

    function list_to_data(values){
        return values.map((value, index) => ({ x: index, y: value }))
    }

    function hline(y, x_min, x_max){
        return [
            {x: x_min, y: y},
            {x: x_max, y: y}
        ]
    }

    function updateVarianceChart() {
        chart.data.datasets[0].data = list_to_data(variances);
        chart.data.datasets[1].data = list_to_data(variancesSchaetzer);

        chart.data.datasets[2].data = hline(getPopulationStd(), 0, variances.length);
        chart.data.datasets[3].data = hline(getSampleStdMean(), 0, variances.length);
        chart.data.datasets[4].data = hline(getSchaetzerStdMean(), 0, variancesSchaetzer.length);
        chart.update();
    }

    function updatePopChart() {
        popChart.data.datasets[]
    }

    function updateText(id, value, fixed=2){
        document.getElementById(id).textContent = value.toFixed(fixed);
    }

    function getPopulationMean(){
        return mean(getAllInputs())
    }

    function getSampleMean(){
        return mean(getSelectedInputs())
    }

    function getPopulationStd(){
        return std(getAllInputs())
    }

    function getSampleStd(){
        return std(getSelectedInputs(), 0)
    }

    function getSampleStdMean(){
        return mean(variances)
    }

    function getSchaetzerStd(){
        return std(getSelectedInputs(), 1)
    }

    function getSchaetzerStdMean(){
        return mean(variancesSchaetzer)
    }

    function updateResults(){
        updateText("population-mean", getPopulationMean())
        updateText("sample-mean", getSampleMean())
        updateText("population-std", getPopulationStd())
        updateText("sample-std", getSampleStd())
        updateText("sample-std-mean", getSampleStdMean())
        updateText("schaetzer-std", getSchaetzerStd())
        updateText("schaetzer-std-mean", getSchaetzerStdMean())
    }
        
    initilizeButtons()
    insertRandomValues()
    initilizeVarianceChart()
    initilizePopulationChart()
}); 
</script>
<style>

.sample-button {
    padding: 10px 20px;
    background: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background 0.3s;
}

.sample-button:hover {
    background: #45a049;
}

.sample-button:disabled {
    opacity: 0.7;
    cursor: not-allowed;
}

</style>
</head><body>
<div class="container">
    <div id="value-list">
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
        <div class="value-row">
            <input type="number" class="value-input"> 
            <input type="checkbox" class="sample-checkbox">
        </div>
    </div>
    <div class="result-section">
        <div class="result-row">
            <strong>Mittelwert der Grundgesamtheit:</strong> 
            <span id="population-mean">0</span>
        </div>
        <div class="result-row">
            <strong>Mitteilwert der Stichprobe:</strong> 
            <span id="sample-mean">0</span>
        </div>
        <div class="result-row">
            <strong>Standardabweichung der Grundgesamtheit:</strong> 
            <span id="population-std">0</span>
        </div>
        <div class="result-row">
            <strong>Standardabweichung der Stichprobe:</strong> 
            <span id="sample-std">0</span>
        </div>
        <div class="result-row">
            <strong>Durchschnittliche gemessene Standardabweichung der Stichproben:</strong> 
            <span id="sample-std-mean">0</span>
        </div>
        <div class="result-row">
            <strong>Schätzer:</strong> 
            <span id="schaetzer-std">0</span>
        </div>
        <div class="result-row">
            <strong>Durchschnittlich der Schätzer:</strong> 
            <span id="schaetzer-std-mean">0</span>
        </div>
        
    </div>
    <div class="chart-section">
        <canvas id="varianceChart"></canvas>
        <canvas id="populationChart"></canvas>
        <canvas id="sampleChart"></canvas>
        <canvas id="schaetzerChart"></canvas>
    </div>
    <div class="button-section">
        <button class="sample-button" data-samples="1", data-delay="0">1 Stichprobe wählen</button>
        <button class="sample-button" data-samples="10", data-delay="200">10 Stichprobe wählen</button>
        <button class="sample-button" data-samples="100", data-delay="100">100 Stichprobe wählen</button>
        <button class="sample-button" data-samples="1000", data-delay="20">1000 Stichprobe wählen</button>
        <button class="sample-button" data-samples="10000", data-delay="0">10000 Stichprobe wählen</button>
    </div>
</div>
</body></html>
