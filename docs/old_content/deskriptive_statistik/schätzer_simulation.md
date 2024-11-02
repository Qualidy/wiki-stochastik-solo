<html><head><base href="." /><meta http-equiv="content-type" content="text/html; charset=utf-8">
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
document.addEventListener('DOMContentLoaded', function() {
    const valueInputs = document.querySelectorAll('.value-input');
    const checkboxes = document.querySelectorAll('.sample-checkbox');
    let chart;
    let samplePoints = [];
    let useDegreesOfFreedom = 1;
    
    // Initial random values
    valueInputs.forEach(input => {
        input.value = Math.floor(20 + Math.random() * 20);
        updateVariances();
    });

    document.getElementById('freedom-toggle').addEventListener('change', function() {
        useDegreesOfFreedom = this.checked ? 1 : 0;
        samplePoints = [];
        updateVariances();
        updateChart();
        updateAverageDeviation();
    });

    // Initialize chart
    const ctx = document.getElementById('varianceChart');
    chart = new Chart(ctx, {
        type: 'scatter',
        data: {
            datasets: [{
                label: 'Sample Standard Deviations',
                data: samplePoints,
                backgroundColor: 'rgba(54, 162, 235, 0.5)'
            }, {
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

    function updateAverageDeviation() {
        if (samplePoints.length === 0) return;
        
        const populationStdDev = parseFloat(document.getElementById('population-variance').textContent);
        const totalDeviation = samplePoints.reduce((acc, point) => acc + point.y - populationStdDev, 0);
        const averageDeviation = totalDeviation / samplePoints.length;
        
        document.getElementById('average-deviation').textContent = averageDeviation.toFixed(2);
    }

    // Add event listeners
    valueInputs.forEach(input => {
        input.addEventListener('change', () => {
            updateVariances();
            updateChart();
            updateAverageDeviation();
        });
    });

    checkboxes.forEach(checkbox => {
        checkbox.addEventListener('change', () => {
            updateVariances();
            updateChart();
            updateAverageDeviation();
        });
    });

    async function generateSamples(count) {
        const buttons = document.querySelectorAll('.sample-button');
        buttons.forEach(btn => btn.disabled = true);
        
        const values = Array.from(valueInputs).map(input => parseFloat(input.value));
        const populationStdDev = parseFloat(document.getElementById('population-variance').textContent);
        
        for (let i = 0; i < count; i++) {
            const button = document.querySelector(`button[data-samples="${count}"]`);
            button.style.background = `linear-gradient(to right, #4CAF50 ${(i/count)*100}%, #ffffff ${(i/count)*100}%)`;

            checkboxes.forEach(cb => cb.checked = false);
            
            // Generate power set and select random subset
            const powerSet = [[]];
            for (const [index, checkbox] of checkboxes.entries()) {
                const length = powerSet.length;
                for (let i = 0; i < length; i++) {
                    const subset = powerSet[i].concat(index);
                    powerSet.push(subset);
                }
            }
            
            // Filter for subsets with at least 2 elements
            const validSubsets = powerSet.filter(subset => subset.length >= 2);
            const randomSubset = validSubsets[Math.floor(Math.random() * validSubsets.length)];
            
            // Set checkboxes based on random subset
            checkboxes.forEach((checkbox, index) => {
                checkbox.checked = randomSubset.includes(index);
            });
            
            updateVariances();
            updateChart();
            updateAverageDeviation();
            
            await new Promise(resolve => setTimeout(resolve, 200));
        }
        
        buttons.forEach(btn => {
            btn.disabled = false;
            btn.style.background = '';
        });
    }

    function updateChart() {
        const sampleStdDev = parseFloat(document.getElementById('sample-variance').textContent);
        const populationStdDev = parseFloat(document.getElementById('population-variance').textContent);
        
        if (sampleStdDev > 0) {
            samplePoints.push({x: samplePoints.length, y: sampleStdDev});
        }
        
        // Calculate average standard deviation
        const averageStdDev = samplePoints.length > 0 
            ? samplePoints.reduce((acc, point) => acc + point.y, 0) / samplePoints.length 
            : populationStdDev;
        
        chart.data.datasets[0].data = samplePoints;
        chart.data.datasets[1].data = [{x: 0, y: populationStdDev}, {x: samplePoints.length, y: populationStdDev}];
        chart.data.datasets[2].data = [{x: 0, y: averageStdDev}, {x: samplePoints.length, y: averageStdDev}];
        chart.update();

        // Update average std dev display
        document.getElementById('avg-std-dev').textContent = averageStdDev.toFixed(2);
    }

    document.querySelectorAll('.sample-button').forEach(button => {
        button.addEventListener('click', () => {
            generateSamples(parseInt(button.dataset.samples));
        });
    });

    function updateVariances() {
        const values = Array.from(document.querySelectorAll('.value-input')).map(input => parseFloat(input.value));
        const checkboxes = document.querySelectorAll('.sample-checkbox');
        
        const populationMean = values.reduce((a, b) => a + b, 0) / values.length;
        const populationVariance = values.reduce((acc, val) => acc + Math.pow(val - populationMean, 2), 0) / values.length;
        const populationStdDev = Math.sqrt(populationVariance);
        
        const sampleValues = values.filter((_, index) => checkboxes[index].checked);
        
        let sampleStdDev = 0;
        if (sampleValues.length > 1) {
            const sampleMean = sampleValues.reduce((a, b) => a + b, 0) / sampleValues.length;
            const sampleVariance = sampleValues.reduce((acc, val) => acc + Math.pow(val - sampleMean, 2), 0) / 
                (sampleValues.length - useDegreesOfFreedom);
            sampleStdDev = Math.sqrt(sampleVariance);
        }

        document.getElementById('population-variance').textContent = populationStdDev.toFixed(2);
        document.getElementById('sample-variance').textContent = sampleStdDev.toFixed(2);
    }
});
</script>
<style>
.container {
    max-width: 1200px;
    margin: 20px auto;
    padding: 20px;
}

.top-section {
    display: flex;
    gap: 40px;
    margin-bottom: 30px;
}

.input-section, .results-section {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    padding: 20px;
}

.input-section {
    flex: 0 0 300px;
}

.results-section {
    flex: 1;
}

.value-row {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    gap: 10px;
}

.value-input {
    width: 80px;
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
}

.button-section {
    margin: 20px 0;
    display: flex;
    gap: 10px;
}

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

.result-row, .deviation-info {
    margin-bottom: 15px;
    padding: 10px;
    background: #f8f9fa;
    border-radius: 4px;
}

.freedom-toggle {
    margin-bottom: 20px;
    padding: 15px;
    background: #f8f9fa;
    border-radius: 4px;
}

.chart-section {
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

body {
    background: #f0f2f5;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    line-height: 1.5;
}
</style>
</head><body>
<div class="container">
    <div class="top-section">
        <div class="input-section">
            <h2 class="section-heading">Datenpunkte</h2>
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
                <div class="value-row">
                    <input type="number" class="value-input">
                    <input type="checkbox" class="sample-checkbox">
                </div>
            </div>
        </div>

        <div class="results-section">
            <h2 class="section-heading">Auswertung</h2>
            <div class="freedom-toggle">
                <label>
                    <input type="checkbox" id="freedom-toggle" checked>
                    Stichprobenstandardabweichung mit Freiheitsgrad 1 berechnen
                </label>
            </div>
            <div class="result-row">
                <strong>Standardabweichung der Grundgesamtheit:</strong> 
                <span id="population-variance">0</span>
            </div>
            <div class="result-row">
                <strong>Standardabweichung der Stichprobe:</strong> 
                <span id="sample-variance">0</span>
            </div>
            <div class="result-row">
                <strong>Durchschnittliche Standardabweichung:</strong> 
                <span id="avg-std-dev">0</span>
            </div>
            <div class="deviation-info">
                <strong>Durchschnittliche Abweichung:</strong>
                <span id="average-deviation">0</span>
            </div>
        </div>
    </div>

    <div class="button-section">
        <button class="sample-button" data-samples="1">1 Stichprobe wählen</button>
        <button class="sample-button" data-samples="10">10 Stichproben wählen</button>
        <button class="sample-button" data-samples="100">100 Stichproben wählen</button>
    </div>

    <div class="chart-section">
        <canvas id="varianceChart"></canvas>
    </div>
</div>
</body></html>