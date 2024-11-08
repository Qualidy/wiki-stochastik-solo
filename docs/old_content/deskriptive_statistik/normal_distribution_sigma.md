<html><head><base href="/" /><meta charset="UTF-8"/><style>
.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    font-family: Arial, sans-serif;
}

.graph {
    width: 600px;
    height: 300px;
    margin: 20px auto;
}

.controls {
    text-align: center;
    margin: 20px;
}

.slider-container {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
}

#sigma-slider {
    width: 300px;
}

.stats {
    text-align: center;
    font-size: 1.2em;
    margin: 20px;
    color: #333;
}
</style></head><body>
<div class="container">
    <h1>Normalverteilung Visualisierung</h1>

    <div class="controls">
        <div class="slider-container">
            <label for="sigma-slider">Standardabweichungen (σ): </label>
            <input type="range" id="sigma-slider" min="0" max="4" step="0.25" value="1">
            <span id="sigma-value">1.0</span>
        </div>
    </div>
    <div class="graph">
        <svg id="normalCurve" width="600" height="300"></svg>
    </div>
    <div class="stats">
        <p>Datenpunkte innerhalb des markierten Bereichs: <span id="percentage">68.27%</span></p>
    </div>
</div>

<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
const margin = {top: 20, right: 20, bottom: 30, left: 40};
const width = 600 - margin.left - margin.right;
const height = 300 - margin.top - margin.bottom;

const svg = d3.select("#normalCurve")
    .append("g")
    .attr("transform", `translate(${margin.left},${margin.top})`);

function normalPDF(x, mean = 0, std = 1) {
    return Math.exp(-0.5 * Math.pow((x - mean) / std, 2)) / (std * Math.sqrt(2 * Math.PI));
}

const xScale = d3.scaleLinear()
    .domain([-4, 4])
    .range([0, width]);

const yScale = d3.scaleLinear()
    .domain([0, normalPDF(0)])
    .range([height, 0]);

const line = d3.line()
    .x(d => xScale(d))
    .y(d => yScale(normalPDF(d)));

const points = d3.range(-4, 4.1, 0.1);

svg.append("path")
    .datum(points)
    .attr("class", "line")
    .attr("fill", "none")
    .attr("stroke", "#999")
    .attr("stroke-width", 2)
    .attr("d", line);

const xAxis = d3.axisBottom(xScale);
const yAxis = d3.axisLeft(yScale);

svg.append("g")
    .attr("transform", `translate(0,${height})`)
    .call(xAxis);

svg.append("g")
    .call(yAxis);

const areaPathLeft = svg.append("path")
    .attr("class", "highlighted-area")
    .attr("fill", "rgba(0, 0, 255, 0.2)");

const areaPathRight = svg.append("path")
    .attr("class", "highlighted-area")
    .attr("fill", "rgba(0, 0, 255, 0.2)");

function updateGraph(sigma) {
    const leftPts = points.filter(x => x >= -sigma && x <= 0);
    const rightPts = points.filter(x => x >= 0 && x <= sigma);

    const areaGenerator = d3.area()
        .x(d => xScale(d))
        .y0(height)
        .y1(d => yScale(normalPDF(d)));

    areaPathLeft.attr("d", areaGenerator(leftPts));
    areaPathRight.attr("d", areaGenerator(rightPts));

    const percentage = (erf(sigma/Math.sqrt(2)) * 100).toFixed(2);
    document.getElementById("percentage").textContent = `${percentage}%`;
}

function erf(x) {
    const a1 =  0.254829592;
    const a2 = -0.284496736;
    const a3 =  1.421413741;
    const a4 = -1.453152027;
    const a5 =  1.061405429;
    const p  =  0.3275911;

    const sign = (x >= 0) ? 1 : -1;
    x = Math.abs(x);

    const t = 1.0/(1.0 + p*x);
    const y = 1.0 - (((((a5*t + a4)*t) + a3)*t + a2)*t + a1)*t*Math.exp(-x*x);

    return sign * y;
}

const slider = document.getElementById("sigma-slider");
const sigmaValue = document.getElementById("sigma-value");

slider.addEventListener("input", function() {
    const value = parseFloat(this.value);
    sigmaValue.textContent = value.toFixed(2);
    updateGraph(value);
});

updateGraph(1);
</script>
</body></html>