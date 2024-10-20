# Deskriptive Statistik

Deskriptive Statistik ist der Teil der Statistik, der sich mit der Beschreibung und Zusammenfassung von Daten befasst. Sie verwendet Kennzahlen (wie Mittelwert, Median und Standardabweichung), um zentrale Tendenzen und Streuungen von Daten darzustellen. Häufig werden grafische Darstellungen (Diagramme) genutzt, um Muster und Trends in den Daten auf einen Blick sichtbar zu machen. Deskriptive Statistik **beschreibt** die Daten nur. Wenn man irgendwelche Schlussfolgerungen machen will, nutzt man die Inferenzstatistik.

_Beispiel_   
Im Folgenden wurden von 6 Menschen die Körpergrößen notiert.

|Körpergröße |
|-|
|172|
|183|
|191|
|156|
|183|
|207|

Kennzahlen aus der deskriptiven Statisik:  
Durchschnitt = 182  
Häufigster Wert = 183  

_Aufgabe_  
Welche Kennzahlen könntet ihr euch noch vorstellen?

_Aufgabe_  
Woher kommt das Wort _deskriptiv_ bei der deskriptiven Statistik?  

Es gibt zwei verschiedene Arten von Werten, die in der deskriptiven Statistik immer wieder vorkommen. Das sind zum einen Lagemaße, welche zum Beispiel ein besonders typischer oder zentraler Wert des Datensatzes sein können, und zum anderen Streumaße, welche beschreiben, wie sehr sich die Daten von einander unterscheiden. Wir werden nun im folgenden diese verschiedenen Maße durchgehen.

 



## Anwendungsfälle der Lagemaße

### Mittelwert (Durchschnitt):

_Anwendungsfall:_ Für metrische Daten (z.B. Größe, Gewicht), wenn die Daten eine symmetrische Verteilung haben.  
_Beispiel:_ Durchschnittsgröße einer Gruppe von Personen  
_Achtung:_ Empfindlich gegenüber Ausreißern - sehr große oder kleine Werte können den Mittelwert stark beeinflussen.  

### Median:  
_Anwendungsfall:_ Für metrische oder ordinale Daten, wenn die Daten asymmetrisch verteilt sind.  
_Beispiel:_ Median-Einkommen in einer Region, um extreme Spitzengehälter nicht zu stark zu gewichten.  

### Modus:
_Anwendungsfall:_ Für alle Datenarten möglich  
_Beispiel:_ Häufigste Schuhgröße in einem Laden oder häufigste Umfrageantwort  

_Beispiel: Mittelwert oder Median_  

|Produktpreis (in Euro)|
|-|
|11|
|9|
|13|
|189|
|14|
|16|
|7|

$$ Durchschnitt = 37 $$  

$$ Median = 13 $$

Bei diesem Beispiel fällt auf, dass der Durchschnitt wesentlich höher ist als die meisten Datenpunkte. Ein einzelner Ausreißer sorgt für einen hohen Durchschnitt. Möchte man eine Preisempfehlung machen, dann repräsentiert in diesem Fall der Median den Datensatz besser.  

_Aufgabe: Lagemaße_  
Bestimme das arithmetische Mittel, den Median und den Modus, wenn möglich. Wähle aus, welches Lagemaß am besten repräsentiert, und begründe deine Wahl. Ordne jedem Datensatz das passende Skalenniveau zu.

a) Die Ergebnisse eines Tests in einer Schulklasse lauten:  

$$(49,45,95,58,52,57,56,61,49,52)$$

b) Die Mitarbeiter einer Firma haben ihre Fahrtzeiten in Minuten notiert:  

$$(12, 37, 21, 25, 30, 12, 19, 25, 15, 12 ,21)$$

c) Ein Modegeschäft hat in der letzten Woche folgende T-Shirt Größen verkauft:

$$(𝑀, 𝑆, 𝑀, 𝑀, 𝑋𝐿, 𝐿, 𝐿, 𝑋𝐿, 𝑆, 𝑆, 𝐿, 𝑀)$$

d) Bei einer Umfrage nach der Lieblingssportart wurden folgende Antworten gegeben:

$$(Tennis, Fußball, Schwimmen, Schwimmen, Tennis, Fußball, Fußball, Volleyball, Schwimmen, Volleyball, Volleyball)$$

## Spannweite

Die Spannweite (auch Range genannt) ist ein einfaches Maß für die Streuung von Daten. Sie gibt an, wie groß der Abstand zwischen dem größten und dem kleinsten Wert in einem Datensatz ist. Um die Spannweite zu berechnen, zieht man den kleinsten Wert vom größten ab. Die Spannweite zeigt, wie weit die Werte auseinanderliegen, gibt aber keine Informationen darüber, wie die Werte dazwischen verteilt sind. Sie ist anfällig für Ausreißer, da nur die extremen Werte berücksichtigt werden.  

_Beispiel_  
Im Folgenden sind die Alter einer Familie notiert worden.  

|Alter (in Jahren)|
|-|
|7|
|32|
|31|
|4|
|67|
|71|

$$ Spannweite = 71 - 4 = 67 $$

Die Alter in dieser Familie streuen also über eine Spannweite von 67 Jahren.  

_Aufgabe: Spannweite_  
Bestimme die Spannweite folgender Datensätze.  

a) $(4, 18, 14, 27, 19, 12)$  
b) $(−3,−20,−11, 0)$  
c) $(3, 3, 5,−2, 7, 5,−2)$  
d) $(65,−48,−1, 55,−31, 15)$  


## Interquartilabstand
Der Interquartilabstand (IQA) ist ein Maß für die Streuung von Daten und gibt an, wie weit die mittleren 50% der Daten verteilt sind. Er wird berechnet, in dem man den sortierten Datensatz in der Mitte teilt, den Median beider Teile berechnet und anschließend den unteren vom oberen subtrahiert.  

_Beispiel mit gerader Anzahl an Werten_

||
|-|
|1|
|1|
|3|
|4|
|4|
|6|
|7|
|8|
|8|
|9|

Nach Teilung in der Mitte erhält man folgenden zwei Datensätze:  

|||
|-|-|
|1|6|
|1|7|
|3|8|
|4|8|
|4|9|

$$ linker\ Median = 3 $$

$$ rechter\ Median = 8 $$

$$ IQA = 8 - 3 = 5 $$

_Beispiel mit ungerade Anzahl an Werten_

||
|-|
|1|
|2|
|2|
|3|
|4|
|5|
|5|
|7|
|8|

Um zwei gleichgroße Datensätze zu erhalten, wird bei einer ungeraden Anzahl der mittlere Wert ignoriert.  

|||
|-|-|
|1|5|
|2|5|
|2|7|
|3|8|

Der mittlere Wert "4" ist also in keinem der beiden Sätze mehr enthalten.  

$$ linker\ Median = \frac{2+2}{2} = 2 $$

$$ rechter\ Median = \frac{5+7}{2} = 6 $$

$$ IQA = 6 - 2 = 4 $$

_Aufgabe: IQA_  

Bestimme den IQA folgender Datensätze.  
a) $(12, 32, 53, 32, 15, 28, 31)$  
b) $(32, 41, 21, 14, 19, 25, 71, 5)$  
c) $(17, 19, 11, 9, 21, 13, 20, 10, 5)$  
d) $(51, 32, 41, 44, 25, 28, 30, 11, 3)$  

## Schiefe

Die Schiefe beschreibt, wie asymmetrisch eine Verteilung von Daten ist. Es gibt drei Typen von Schiefe:  

1. Rechtsschiefe (positive Schiefe): Der rechte Teil der Verteilung ist länger, und die meisten Werte liegen auf der linken Seite.  
2. Linksschiefe (negative Schiefe): Der linke Teil der Verteilung ist länger, und die meisten Werte liegen auf der rechten Seite.  
3. Symmetrisch: Die Verteilung ist gleichmäßig auf beide Seiten verteilt.  

Die Schiefe hilft dabei zu verstehen, ob extreme Werte auf einer Seite häufiger auftreten.  

Qualitativ lässt sich die Schiefe mithilfe des Medians und des Mittelwertes bestimmen. Ist der Mittelwert größer als der Median, dann ist der Datensatz rechtsschief, ist er kleiner als der Median, dann ist es linksschief. Sind Mittelwert und Median gleich, ist der Datensatz symmetrisch.
Da es sich hierbei um ein Streuungsmaß handelt, lässt sich dazu natürlich ein passender Wert berechnen. Die Formel lautet wie folgt:

$$ y_m = \frac{1}{n\sigma^3} \sum_{i = 1}^n(x_i - \bar{x})^3 $$

- $y_m$ ist das Symbol für die Schiefe
- $n$ ist die Anzahl an Werten
- $x_i$ ist ein einzelner Wert
- $\bar{x}$ ist der Mittelwert
- $\sigma$ ist die Standardabweichung

Da die Standardabweichung zu diesem Zeitpunkt noch nicht behandelt wurde, kommen wir später auf diese Formel zurück.  

_Aufgabe: Schiefe_

Ordne die Begriffe rechtsschief, linksschief und symmetrisch den folgenden Datensätze zu.
a) $(30, 37, 29, 33, 52, 64, 31, 30, 35)$  
b) $(11, 15, 19, 13, 10, 17, 20, 15)$  
c) $(19, 23, 18, 22, 13, 11, 21, 19)$  

## Stichprobe und Grundgesamtheit
In der Statistik müssen wir zwischen Grundgesamtheit (oft auch Population) und Stichproben unterscheiden. Grundsätzlich interessiert man sich meistens für die Grundgesamtheit. Da die aber sehr groß sein kann, ist es praktischer eine Stichprobe zu untersuchen, um anhand derer Schlüsse für die Grundgesamtheit zu schließen.  
Für Grundgesamtheit und Stichproben werden oft die gleichen Kennzahlen genutzt. Um beide gut auseinander halten zu können, nutzt man unterschiedliche Symbole für die jeweiligen Kennzahlen.

- Die Anzahl der Datenpunkte wird für die Grundgesamtheit mit $N$ abgekürzt, für die Stichprobe mit $n$.  
- Der Mittelwert nutzt für eine Stichprobe das Symbol $\bar{x}$ und für die Grundgesamtheit $\mu$.
- Die Standardabweichung der Grundgesamtheit nutzt $\sigma$, die der Stichprobe wird mit $s$ betitelt.


## Varianz und Standardabweichung

Varianz und Standardabweichung sind Streumaße dafür, wie stark die Daten in einem Datensatz durchschnittlich um den Mittelwert streuen.  

### Varianz der Grundgesamtheit

$$ \sigma^2 = \frac{1}{N} \sum_{i=1}^N (x_i - \mu)^2 $$

Die Standardabweichung beschreibt die durchschnittliche quadratische Abweichung der Datenpunkte vom Mittelwert.  
Zentral in der Formel der Varianz ist der Abstand zwischen einem Datenpunkt und dem Mittelwert $x_i - \mu$.  
Bei dieser Rechnung können sowohl negative wie auch positive Abstände entstehen. In welche Richtung der Datenpunkt vom Mittelwert abweicht, soll aber keine Rolle spielen. Zusätzlich sollen starke Abweichungen vom Mittelwert ein stärkeres Gewicht bekommen. Daher wird der Abstand quadriert, um diese beiden Ziele zu erreichen $(x_i - \mu)^2$.  
Dieser quadrierte Abstand wird für jeden einzelnen Datenpunkt berechnet und dann aufsummiert $\sum_{i=1}^N$.  
Schlussendlich wird aus dieser Gesamtsumme der Durchschnitt berechnet, in dem durch die Anzahl der Datenpunkte geteilt wird $\frac{1}{N}$.  

_Beispiel_

Ein Firmeninhaber hat die Gewinne seiner 4 Filialen notiert.

|Gewinn (in Euro)|
|-|
|800|
|1200|
|1300|
|1700|

$$ \mu = \frac{800 + 1200 + 1300 + 1700}{4} = 1250 $$

$$ \sigma^2 = \frac{(800 - 1250)^2 + (1200 - 1250)^2 + (1300 - 1250)^2 + (1700 - 1250)^2}{4} = 102.500 $$

Die Varianz liegt hier also bei 102.500.  

_Aufgabe: Varianz einer Grundgesamtheit_

Berechne die Varianz der folgenden Grundgesamtheiten.  
a) $(14, 15, 15, 18)$  
b) $(14, 15, 15, 30)$  

Der Wert der Varianz ist schwer zu interpretieren. Das liegt am Quadrieren des Abstandes. Im Beispiel des Firmeninhabers ist die Einheit der Varianz €$^2$.  
Die Einheit der Varianz ist also das Quadrat der Einheit eines Datenpunktes. Um diese Diskrepanz aufzulösen, wird die Standardabweichung hinzugezogen.

### Standardabweichung einer Grundgesamtheit

$$ \sigma = \sqrt{\frac{1}{N} \sum_{i=1}^N (x_i - \mu)^2} $$

Die Standardabweichung ist nichts anderes als die Wurzel der Varianz. Sie beschreibt den durchschnittliche Abstand der Datenpunkte um den Mittelwert. Im Gegensatz zur Varianz hat sie die gleiche Einheit wie die Datenpunkte.  

_Beispiel_

Beim Beispiel des Firmeninhabers hat sich eine Varianz von 102500 ergeben. Um nun die passende Standardabweichung zu berechnen, muss nur noch die Wurzel gezogen werden.  

$$ \sigma = \sqrt{102500} \approx 320 $$

|Gewinn (in Euro)|
|-|
|800|
|1200|
|1300|
|1700|

Vergleicht man die Standardabweichung nun mit dem Datensatz, dann fällt auf, dass die Standardabweichung viel anschaulich die Streuung beschreibt als die Varianz. Das liegt daran, dass die Quadrierung in der Varianz für die Standardabweichung aufgelöst wurde.  

_Aufgabe: Standardabweichung einer Grundgesamtheit_

Berechne die Standardabweichung der folgenden Grundgesamtheiten.  
a) $(14, 15, 15, 18)$  
b) $(14, 15, 15, 30)$  

### Varianz einer Stichprobe

$$ s^2 = \frac{1}{n - 1} \sum_{i=1}^n (x_i - \bar{x})^2 $$

Wenn von der Varianz einer Stichprobe die Rede ist, dann meint man damit eigentlich eine Schätzung der Varianz der Grundgesamtheit anhand einer Stichprobe und **nicht** die Varianz der Stichprobe selbst. Wenn man die tatsächlichen Varianzen aller möglichen Stichproben einer Grundgesamtheit berechnet, fällt auf, dass man öfter unterhalb der Varianz der Grundgesamtheit liegt als darüber. Das liegt daran, dass die Ausreißer, welche einen stärkeren Einfluss auf die Varianz haben, seltener in einer Stichprobe vorhanden sind. Hier ist also in der Mathematik selbst ein systematischer Fehlschätzung. Um diesem Fehler entgegenzuwirken, wird ein Korrekturfaktor genutzt $\frac{1}{n - 1}$.  
Je kleiner die Stichprobe, desto größer ist der Einfluss dieser Korrektur. Das kann man sich dadurch erklären, dass eine große Stichprobe die Grundgesamtheit besser wiederspiegelt und daher eine geringere Korrektur benötigt. Ansonsten ist die Formel identisch zur Varianz einer Grundgesamtheit.  

_Beispiel_

Ein Firmeninhaber hat 10 Filialen. Er hat in einer Stichprobe die Gewinne von 4 Filialen notiert.

|Gewinn (in Euro)|
|-|
|800|
|1200|
|1300|
|1700|

$$ \bar{x} = \frac{800 + 1200 + 1300 + 1700}{4} = 1250 $$

$$ s^2 = \frac{(800-1250)^2 + (1200-1250)^2 + (1300-1250)^2 + (1700-1250)^2}{4-1} $$

Die Varianz der Stichprobe (eigentlich die Schätzung der Varianz der Grundgesamtheit anhand der Stichprobe) beträgt also ungefähr 136.667.

_Aufgabe: Varianz einer Stichprobe_

Berechne die Varianz der folgenden Stichproben.
(Berechne eine Schätzung der Varianz der Grundgesamhtheit anhand folgender Stichproben.)   
a) $(14, 15, 15, 18)$  
b) $(14, 15, 15, 30)$  

### Standardabweichung einer Stichprobe

$$ s = \sqrt{\frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})} $$

Auch bei der Standardabweichung einer Stichprobe ist in der Regel eine Schätzung der Standardabweichung der Grundgesamtheit anhand der Stichprobe gemeint. Das heißt es kommt der gleiche Korrekturfaktor zum Einsatz wie bei der Varianz einer Stichprobe.  

_Beispiel_  

Nimmt man die Varianz des vorherigen Beispiels, erhält man folgende
Standardabweichung.  

$$ s = \sqrt{13667} \approx 370 $$

_Aufagbe: Standardabweichung einer Stichprobe_

Berechne die Standardabweichung der folgenden Stichproben.  
(Berechne eine Schätzung der Standardabweichung der Grundgesamhtheit anhand folgender Stichproben.)   
a) $(14, 15, 15, 18)$  
b) $(14, 15, 15, 30)$  

## Verschiebung und Skalierung

Um das Verständnis der Lagemaße und Streumaße besser zu verstehen, lohnt es sich Datensätze zu verschieben bzw. zu skalieren.

### Verschiebung

Bei einer Verschiebung eines Datensatzes wird jeder Datenpunkt mit demselben Wert subtrahiert bzw. addiert.  


_Beispiel_  
Datensatz vor Verschiebung:

||
|-|
|2|
|2|
|5|
|6|
|9|
|12|

$$ Mittelwert = 6 $$

$$ Median = 5,5 $$

$$ Modus = 2 $$

$$ Spannweite = 10 $$

$$ IQA = 7 $$

$$ Varianz = 13 $$

Nun wird jeder Datenpunkt mit 3 addiert:

||
|-|
|5|
|5|
|8|
|9|
|12|
|15|

_Aufgabe: Verschiebung_  

Wie verändern sich die Kennzahlen nach der Verschiebung?  

$$ Mittelwert = 9 $$

$$ Median = 8,5 $$

$$ Modus = 5 $$

$$ Spannweite = 10 $$

$$ IQA = 7 $$

$$ Varianz = 13 $$

Man kann beobachtet, dass die Lagemaße sich gleichermaßen wie die Datenpunkte verschoben haben. Die Streumaße sind dabei unverändert.

### Skalierung

Bei einer Skalierung wird jeder Datenpunkt mit dem selben Wert multipliziert bzw. dividiert.

_Beispiel_  
Datensatz vor Verschiebung:

||
|-|
|2|
|2|
|5|
|6|
|9|
|12|

$$ Mittelwert = 6 $$

$$ Median = 5,5 $$

$$ Modus = 2 $$

$$ Spannweite = 10 $$

$$ IQA = 7 $$

$$ Varianz = 13 $$

Jeder Datenpunkt soll mit 2 multipliziert werden:

||
|-|
|4|
|4|
|10|
|12|
|18|
|24|

_Aufgabe: Skalierung_  

Wie verändern sich die Kennzahlen nach der Skalierung?  

$$ Mittelwert = 12 $$

$$ Median = 11 $$

$$ Modus = 4 $$

$$ Spannweite = 20 $$

$$ IQA = 14 $$

$$ Varianz = 52 $$

## Statistische Momente

### nicht-standardisierte Momente

Die statistische Momente haben wir teilweise in dieser Schulung schon kennen gelernt. Es sind neue Fachbegriffe, die die unterschiedlichen Kennzahlen zusammenführen. Die ersten beiden Momente fallen dabei ein wenig aus dem Muster, wie wir gleich sehen werden.

_Allgemeine Formel_

$$ m_k = \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^k $$

_Erstes statistisches Moment: Mittelwert_

$$ m_1 = \frac{1}{n} \sum_{i=1}^n x_i $$

Hier wird noch nicht die Differenz der einzelnen Datenpunkte zum Mittelwert bestimmt, da das erste Moment ja selbst der Mittelwert ist. Würde man hier jedes mal den Abstand zum Mittelwert berechnen, wäre das Ergebnis immer 0 (,probier es doch mal aus). Das erste Moment bedarf noch keiner Standardisierung.

_Zweites statistisches Moment: Varianz_

$$ m_2 = \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2 $$

Das zweite statistische Moment, die Varianz, wird ebenfalls noch nicht standardisiert. Das liegt daran, dass bei den folgenden Momenten mit Hilfe der Varianz bzw. Standardabweichung standardisiert wird. Würde man die Varianz mit Hilfe der Varianz standardisieren, wäre das Ergebnis immer 0 und hätte damit jegliche Aussagekraft verloren.

### standardisierte Momente

_Allgemeine standardisierte Formel_

$$ m_k = \frac{1}{\sigma^k n} \sum_{i=1}^n (x_i - \bar{x})^k $$

_Drittes statistische Moment: Schiefe_

$$ m_3 = \frac{1}{\sigma^3 n} \sum_{i=1}^n (x_i - \bar{x})^3 $$

Das dritte statistische Moment ist die Schiefe. Diese wurde qualitativ bereits eingeführt. Als Erinnerung: die Schiefe beschreibt wie asymmetrisch eine Verteilung ist. Ab dem dritten statistischen Moment wird standardisiert. Das bedeutet, dass wir das Moment durch die Standardabweichung hoch des entsprechenden Grades dividieren. Der Grund für die Standardisierung ist, dass die Momente mit zunehmenden Grad immer größer werden (siehe $(x_i - \bar{x})^3$). Die Standardisierung sorgt dafür, dass die Momente handhabbare Werte annehmen.

_Viertes statistisches Moment: Kurtosis_

$$ m_4 = \frac{1}{\sigma^4 n} \sum_{i=1}^n (x_i - \bar{x})^4 $$

Die Kurtosis ist die eine neue Kennzahl, die hier eingeführt wird. Eine hohe Kurtosis beudetet, dass es viele Extremwerte, also Ausreißer, gibt. Wenn zum Beispiel bei einer Stichprobe viele Menschen über 2 Meter oder unter 1,60 Meter sind, dann hat die Stichprobe eine hohe Kurtosis. Gibt es wenige Extrempunkte ist die Kurotsis entsprechend klein.

