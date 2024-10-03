# Lineare Regression

Lineare Regression ist ein statistisches Verfahren, mit dem der Zusammenhang zwischen zwei Variablen modelliert wird. Dabei versucht man, eine Gerade (auch "Regressionsgerade" genannt) durch die Datenpunkte zu legen, um zu zeigen, wie eine Variable (abhängige Variable) durch eine andere (unabhängige Variable) beeinflusst wird.

_Beispiel_  
_Stell dir vor, du willst den Zusammenhang zwischen der Anzahl von Stunden, die jemand lernt, und der Note, die er oder sie bekommt, untersuchen. Die lineare Regression hilft, diesen Zusammenhang zu quantifizieren und zu verstehen, wie sich die Note verändert, wenn die Lernstunden steigen oder sinken._

|Lernstunden|Punktzahl|
|-|-|
|2|24|
|4|37|
|6|62|
|8|79|
|10|?|

Die Regressionsgerade hat wie jede andere Gerade die allgemeine Form:

$$ y = mx + b $$

Die Parameter $m$ und $b$ sollen für die Regressionsgerade nun so gewählt werden, dass die Abstände der Datenpunkte möglichst gering ist. Dazu werden folgenden Formeln benutzt:

$$ m = \frac{n \sum xy - \sum x \sum y}{n \sum x^2 - (\sum x)^2} $$

$$ b = \frac{\sum y - m \cdot \sum x}{n} $$

_Beispiel_  
_Berechnung von $m$ aus dem Datensatz:_

$$ \sum xy = 2 \cdot 24 + 4 \cdot 37 + 6 \cdot 62 + 8 \cdot 79 = 1200 $$

$$ \sum x = 20 $$

$$ \sum y = 202 $$

$$ \sum x \sum y = 20 \cdot 202 = 4040 $$

$$ \sum x^2 = 2^2 + 4^2 + 6^2 + 8^2 = 120 $$

$$ (\sum x)^2 = 20^2 = 400 $$

- $n$ ist die Anzahl an gegebenen Datenpunkten: $n = 4$

$$ m = \frac{4 \cdot 1200 - 4040}{4 \cdot 120 - 400} = 9,5 $$

_Berechnung von $b$:_

$$ b = \frac{202 - 9,5 \cdot 20}{4} = 3 $$

_Die entsprechende Regressionsgerade ist also:_

$$ y = 9,5x + 3 $$

_Wir können damit den fehlenden Wert $x=10$ berechnen._

$$ y = 9,5 \cdot 10 + 3 = 98 $$

_Wenn man also 10 Stunden lernt, dann kann mit 98 Punkten rechnen._

## Korrelationskoeffizient

Der Korrelationskoeffizient ist eine Zahl, die anzeigt, wie stark zwei Variablen miteinander zusammenhängen. Er gibt uns eine Vorstellung davon, ob und wie gut sich die eine Variable vorhersagen lässt, wenn wir die andere kennen.

$$ r_{xy} = \frac{n \sum xy - \sum x \sum y}{\sqrt{n \sum x^2 - (\sum x)^2} \sqrt{n \sum y^2 - (\sum y)^2}} $$

Bei der sogenannten Pearson-Korrelation entsteht ein Wert aus dem Interval $[-1,1]$. Der Wert $1$ sagt aus, dass die beiden Größen $x$ und $y$ perfekt proportional zueinander sind. Je größer $x$ wird, desto größer wird auch $y$. Ergibt die Korrelation einen Wert von $0$, dann heißt das, dass es keinen linearen Zusammenhang zwischen $x$ und $y$ gibt. Bei einem Wert von $-1$, handelt es sich ebenfalls um eine perfekte Proportionalität, nur dass die Steigung der Regressionsgeraden dann negativ ist. Je größer $x$ ist, desto kleiner wird dann $y$.

<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interaktives Korrelationsdiagramm</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js"></script>
    <style>
        #chart-container {
            width: 80%;
            max-width: 600px;
            margin: 20px auto;
        }
        #correlation {
            text-align: center;
            font-size: 18px;
            margin-top: 20px;
        }
        #reset-button {
            display: block;
            margin: 20px auto;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="chart-container">
        <canvas id="scatterChart"></canvas>
    </div>
    <div id="correlation"></div>
    <button id="reset-button">Zurücksetzen</button>

    <script>
        const ctx = document.getElementById('scatterChart').getContext('2d');
        let chart;
        let points = [];

        function initChart() {
            chart = new Chart(ctx, {
                type: 'scatter',
                data: {
                    datasets: [{
                        data: points,
                        backgroundColor: 'rgba(75, 192, 192, 0.6)'
                    }]
                },
                options: {
                    scales: {
                        x: {
                            type: 'linear',
                            position: 'bottom',
                            min: 0,
                            max: 100
                        },
                        y: {
                            min: 0,
                            max: 100
                        }
                    },
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `(${context.parsed.x.toFixed(2)}, ${context.parsed.y.toFixed(2)})`;
                                }
                            }
                        }
                    },
                    onClick: handleClick
                }
            });
        }

        function handleClick(event, elements, chart) {
            const canvasPosition = Chart.helpers.getRelativePosition(event, chart);
            
            const dataX = chart.scales.x.getValueForPixel(canvasPosition.x);
            const dataY = chart.scales.y.getValueForPixel(canvasPosition.y);
            
            points.push({x: dataX, y: dataY});
            updateChart();
        }

        function updateChart() {
            chart.data.datasets[0].data = points;
            chart.update();
            updateCorrelation();
        }

        function calculateCorrelation() {
            if (points.length < 2) return 0;

            const n = points.length;
            let sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0, sumY2 = 0;

            for (let point of points) {
                sumX += point.x;
                sumY += point.y;
                sumXY += point.x * point.y;
                sumX2 += point.x * point.x;
                sumY2 += point.y * point.y;
            }

            const numerator = n * sumXY - sumX * sumY;
            const denominator = Math.sqrt((n * sumX2 - sumX * sumX) * (n * sumY2 - sumY * sumY));

            return denominator === 0 ? 0 : numerator / denominator;
        }

        function updateCorrelation() {
            const correlation = calculateCorrelation();
            document.getElementById('correlation').textContent = `Pearson-Korrelationskoeffizient: ${correlation.toFixed(4)}`;
        }

        function resetChart() {
            points = [];
            updateChart();
        }

        document.getElementById('reset-button').addEventListener('click', resetChart);

        initChart();
    </script>
</body>
</html>


_Aufgabe: Korrelationskoeffizient_  
_Berechne den Korrelationskoeffizient des folgenden Datensatzes._

|Lernstunden|Punktzahl|
|-|-|
|2|24|
|4|37|
|6|62|
|8|79|


## Fehlermetriken der linearen Regression

### Residuen 
Residuen sind die Abweichungen oder Fehler, die entstehen, wenn man ein Modell (z.B. eine Regressionsgerade) verwendet, um Daten vorherzusagen. Sie zeigen, wie weit die tatsächlichen Datenpunkte von den vorhergesagten Werten des Modells entfernt sind.

Residuum = Tatsächlicher Wert - Vorhergesagter Wert

$$ e_i = y_i - y(x_i) $$

- $e_i$ ist das Residuum vom Wert $x_i$ 
- $y_i$ ist der tatsächliche y-Wert aus dem Datensatz
- $y(x_i)$ ist der durch die Regressionsgerade vorhergesagte Wert

_Beispiel_

|Lernstunden|Punktzahl|
|-|-|
|2|24|
|4|37|
|6|62|
|8|79|

$$ y(x) = 9,5x + 3 $$

$$ e_1 = 24 - (9,5 \cdot 2 + 3) = 2 $$

$$ e_2 = 37 - (9,5 \cdot 4 + 3) = -4 $$

$$ e_3 = 62 - (9,5 \cdot 6 + 3) = 2 $$

$$ e_4 = 79 - (9,5 \cdot 8 + 3) = 0 $$

Die Summe aller Residuen ergibt dabei immer $0$, weil die Regressionsgerade genau in der Mitte der Datenpunkte liegt. Wir können damit also die Abweichungen einzelner Datenpunkte beschreiben, als Maß für die durchschnittliche Abweichung aller Datenpunkte von der Regressionsgerade eignen sich die Residuen nicht.

### Mittlerer quadratischer Fehler

Der mittlere quadratische Fehler (englisch: Mean Squared Error, kurz MSE) ist ein Maß dafür, wie gut ein Modell Daten vorhersagt. Er zeigt, wie groß im Durchschnitt die quadratischen Fehler (Abweichungen) zwischen den tatsächlichen Werten und den vom Modell vorhergesagten Werten sind.

$$ MSE = \frac{1}{n} \sum_{i=1}^n (y_i - y(x_i))^2 $$

Diese Formel sollte uns bekannt vorkommen, denn sie ähnelt sehr der Formel der Varianz. Genau wie bei der Varianz wollen wir hier die einzelnen Residuen quadrieren, um zum einen nur positive Werte zu erhalten und zum anderen starken Abweichungen ein größeres Gewicht zuzuteilen. 

### Mittlerer absoluter Fehler

Der mittlere absolute Fehler (englisch: Mean Absolute Error, kurz MAE) ist ein Maß dafür, wie genau ein Modell die Daten vorhersagt. Er gibt die durchschnittliche Abweichung zwischen den tatsächlichen Werten und den vorhergesagten Werten an, und zwar als absoluter Betrag (ohne Vorzeichen).

$$ MAE = \frac{1}{n} \sum_{i=1}^n |y_i - y(x_i)| $$

Anstatt die einzelnen Residuen zu quadrieren, können wir auch den Durchschnitt der Betragswerte der Residuen berechnen. Bei diesem Vorgehen wird großen Abweichungen kein höheres Gewicht gegeben als kleinen Abweichungen.

### Wurzel des mittleren quadratischen Fehlers

Die Wurzel des mittleren quadratischen Fehlers wird als Root Mean Squared Error (RMSE) bezeichnet. Sie ist ein häufig verwendetes Maß, um die Genauigkeit eines Modells zu bewerten, und gibt die durchschnittliche Größe der Fehler zwischen den vorhergesagten und den tatsächlichen Werten an.

$$ RMSE = \sqrt{MSE} = \sqrt{\frac{1}{n} \sum_{i=1}^n (y_i - y(x_i))^2} $$

Diese Formel ist analog zur Formel der Standardabweichung. Genau wie bei der Standardabweichung kann man auch hier die 68-95-99-Regel verwenden. Das bedeutet also, dass zu 68% ein beliebiger Fehler innerhalb eines RMSE's um die Regressionvorhersage liegt. Oder anders gesagt, 68% der Datenpunkte liegen einen RMSE entfernt von der Regressionsgeraden. Das gleiche gilt natürlich mit 95% und der zweifache RMSE und 99% und der dreifache RMSE.

## Determinationskoeffizient

Der Determinationskoeffizient (auch bekannt als $r^2$ oder Bestimmtheitsmaß) ist ein Maß dafür, wie gut ein statistisches Modell die Daten erklärt. Er zeigt an, wie viel der Varianz (Streuung) in den Daten durch das Modell erklärt wird.

Für lineare Regressionen mit der Pearson-Korrelation lässt sich der Determinationskoeffizient sehr einfach berechnen. In diesem Fall ist Der Determinationkoeffizient nämlich einfach das Quadrat des Korrelationskoeffizienten.

$$ Determinationskoeffizient = r^2 $$

- $r$ ist der Korrelationskoeffizient von Pearson
  
Der Determinationskoeffizient nimmt Werte aus dem Intervall $[0,1]$ an. Dabei bedeutet ein Wert von 1 gibt an, dass das verwendete Regressionsmodell perfekt zu den gegebenen Daten passt. Ein Wert von 0 sagt aus, dass zwischen dem genutzten Modell und den tatsächlichen Daten keinerlei zusammenhang besteht.

Hat man es mit einem anderen Regressionsmodell zu tun, dann berechnet sich der Determinationskoeffizient wie folgt.  
Das Vorgehen vergleicht das genutzte Regressionsmodell mit dem einfachsten Regressionsmodell, nämlich für jede unabhängige Variable $x$ den gleichen Mittelwert der abhängigen Variablen $y$ vorherzusagen.  
Dafür wird die Summe der quadratischen Residuen zum verwendeten Regressionsmodell (Summe quadratischer Risiduen: SQR) und die Summe der quadratischen Residuen zum einfachsten Regressionsmodell (totale Quadratsummen: TQR), dem Mittelwert, berechnet. Der Determinationskoeffizient ist dann:

$$ r^2 = 1 - \frac{SQR}{TQR} $$

_Beispiel_  

|Lernstunden|Punktzahl|
|-|-|
|2|24|
|4|37|
|6|62|
|8|79|

$$ e_1^2 = 2^2 = 4 $$

$$ e_2^2 = (-4) = 16 $$

$$ e_3^2 = 2^2 = 4 $$

$$ e_4^2 = 0^2 = 0 $$

$$ SQR = \sum_{i=1}^n e_i^2 = 4 + 16 + 4 + 0 = 24 $$

$$ \bar{y} = \frac{24 + 37 + 62 + 79}{4} = 50,5 $$

$$ TQR = (24 - 50,5)^2 + (37 - 50,5)^2 + (62 - 50,5)^2 + (79 - 50,5)^2 = 1829 $$

$$ r^2 = 1 - \frac{24}{1829} \approx 0,987 $$

_Wir können mit diesem Wert also nun sagen, dass ungefähr 99% der Varianz um den Mittelwert durch unser Modell erklärt werden kann._

