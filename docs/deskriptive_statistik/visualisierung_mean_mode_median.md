# Visualisierung von Modus, Median und Arithmetischem Mittel

<div id="controls">
    <label><input type="checkbox" id="meanCheckbox" checked> Arithmetisches Mittel</label>
    <label><input type="checkbox" id="medianCheckbox" checked> Median</label>
    <label><input type="checkbox" id="modeCheckbox" checked> Modus</label>
    <label><input type="checkbox" id="discreteCheckbox"> Diskret</label>
</div>

<canvas id="visualization" width="600" height="200"></canvas>

<style>
    #controls {
        margin-bottom: 20px;
        text-align: center;
    }

    canvas {
        border: 1px solid black;
        margin-top: 20px;
        cursor: pointer;
        display: block;
        margin-left: auto;
        margin-right: auto;
    }
</style>

<script>
    const canvas = document.getElementById('visualization'); 
    const ctx = canvas.getContext('2d'); 

    const meanCheckbox = document.getElementById('meanCheckbox'); 
    const medianCheckbox = document.getElementById('medianCheckbox'); 
    const modeCheckbox = document.getElementById('modeCheckbox'); 
    const discreteCheckbox = document.getElementById('discreteCheckbox');

    const gridSize = 40; // Größe der Gitterzellen

    let points = [100, 200, 300, 400, 500].map(x => ({ x, y: Math.random() * canvas.height }));

    function draw() { 
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        // Gitter zeichnen, wenn "Diskret" aktiviert ist
        if (discreteCheckbox.checked) drawGrid();

        points.forEach(point => { 
            ctx.beginPath(); 
            ctx.arc(point.x, point.y, 5, 0, Math.PI * 2); 
            ctx.fillStyle = 'blue'; 
            ctx.fill(); 
        });

        const xValues = points.map(point => point.x).sort((a, b) => a - b); 
        if (meanCheckbox.checked) drawMean(xValues); 
        if (medianCheckbox.checked) drawMedian(xValues); 
        if (modeCheckbox.checked) drawMode(xValues); 
    }

    function drawGrid() {
        ctx.strokeStyle = '#e0e0e0';
        ctx.lineWidth = 1;
        for (let x = 0; x < canvas.width; x += gridSize) {
            ctx.beginPath();
            ctx.moveTo(x, 0);
            ctx.lineTo(x, canvas.height);
            ctx.stroke();
        }
        for (let y = 0; y < canvas.height; y += gridSize) {
            ctx.beginPath();
            ctx.moveTo(0, y);
            ctx.lineTo(canvas.width, y);
            ctx.stroke();
        }
    }

    function snapToGrid(value) {
        return Math.round(value / gridSize) * gridSize;
    }

    function drawMean(xValues) { 
        const mean = xValues.reduce((a, b) => a + b, 0) / xValues.length; 
        drawLine(mean, 'red', 'Mittel'); 
    }

    function drawMedian(xValues) { 
        let median; 
        const middle = Math.floor(xValues.length / 2); 
        if (xValues.length % 2 === 0) 
            median = (xValues[middle - 1] + xValues[middle]) / 2; 
        else 
            median = xValues[middle]; 
        drawLine(median, 'green', 'Median'); 
    }

    function drawMode(xValues) { 
        const freq = {}; 
        xValues.forEach(value => { 
            freq[value] = (freq[value] || 0) + 1; 
        });

        const mode = Object.keys(freq).reduce((a, b) => (freq[a] > freq[b] ? a : b)); 
        if (freq[mode] > 1) 
            drawLine(parseInt(mode), 'purple', 'Modus'); 
    }

    function drawLine(x, color, label) { 
        ctx.beginPath(); 
        ctx.moveTo(x, 0); 
        ctx.lineTo(x, canvas.height); 
        ctx.strokeStyle = color; 
        ctx.lineWidth = 2; 
        ctx.stroke(); 
        ctx.font = '12px Arial'; 
        ctx.fillStyle = color; 
        ctx.fillText(label, x + 5, 20); 
    }

    let draggingPoint = null;

    canvas.addEventListener('mousedown', (event) => { 
        const { offsetX, offsetY, button } = event;
        
        if (button === 0) { // Linksklick zum Hinzufügen oder Ziehen
            draggingPoint = points.find(p => Math.abs(p.x - offsetX) < 10 && Math.abs(p.y - offsetY) < 10);
            if (!draggingPoint) {
                const newX = discreteCheckbox.checked ? snapToGrid(offsetX) : offsetX;
                const newY = discreteCheckbox.checked ? snapToGrid(offsetY) : offsetY;
                points.push({ x: newX, y: newY });
            }
        } else if (button === 2) { // Rechtsklick zum Entfernen
            points = points.filter(p => Math.abs(p.x - offsetX) >= 10 || Math.abs(p.y - offsetY) >= 10);
        }
        
        draw();
    });

    canvas.addEventListener('mousemove', (event) => { 
        if (draggingPoint) { 
            draggingPoint.x = discreteCheckbox.checked ? snapToGrid(event.offsetX) : event.offsetX; 
            draggingPoint.y = discreteCheckbox.checked ? snapToGrid(event.offsetY) : event.offsetY;
            draw(); 
        } 
    });

    canvas.addEventListener('mouseup', () => { 
        draggingPoint = null; 
    });

    // Verhindere das Kontextmenü beim Rechtsklick
    canvas.addEventListener('contextmenu', (event) => {
        event.preventDefault();
    });

    meanCheckbox.addEventListener('change', draw); 
    medianCheckbox.addEventListener('change', draw); 
    modeCheckbox.addEventListener('change', draw); 
    discreteCheckbox.addEventListener('change', draw);

    draw();
</script>
