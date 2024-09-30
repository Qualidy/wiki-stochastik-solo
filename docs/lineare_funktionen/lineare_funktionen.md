# Funktionen

$$ 
f: X ⟶ Y, x ↦ f(x)
$$

``` mermaid
flowchart TB
    subgraph X
    1((1))
    2((2))
    3((3))
    end

    subgraph Y
    A
    B
    C
    D
    end

    1--f-->B
    2--f-->D
    3--f-->D
```

Im Folgenden befassen wir uns mit "Funktionen ersten Grades", den sogenannten linearen Funktionen. 
Zunächst aber die übergeordnete Frage: Was verstehen wir unter einer "Funktion"? 
Eine Funktion $f$ ordnet jedem Element $x$ im *Definitionsbereich* $X$ genau ein Element $y$ im Wertebereich $Y$ zu. Die Funktionsvorschrift $f(x)$ wird meistens abstrakt als Formel angegeben.

_Beispiel_

$$
f: \mathbb{R} \to \mathbb{R} \text{ mit } f(x) = 3x + 2
$$

$$
\begin{align*}
f(4) &= 34 + 2 = 14 \\
f(0) &= 30 + 2 = 2
\end{align*}
$$

* Die Funktion ordnet dem Wert $4$ aus dem Definitionsbereich den Wert $14$ aus dem Wertebereich zu
* Die Funktion ordnet dem Wert $0$ aus dem Definitionsbereich den Wert $2$ aus dem Wertebereich zu

## Lineare Funktionen
Lineare Funktionen haben allgemein die Form $f(x)=mx+b$, wobei $m$ die Steigung und $b$ den **Y-Achsenabschnitt** bzw. den **Startwert** angibt.

_Beispiel_

Ein Taxiunternehmen berechnet für eine Taxifahrt eine **Startgebühr von 3€**  und zusätzlich **2€ pro Kilometer**	&rArr; Somit gilt Startwert b=3, Steigung m=2

Die Informationen werden in die Funktionsgleichung eingesetzt.

$$
\begin{align*}
&rArr; &f(x)&= mx+b \\
&rArr; &f(x)&= 2x+3 \\
&rArr; &y&= 2x+3
\end{align*}
$$

Anstelle von $f(x)$ darf alternativ $y$ geschrieben werden. 

Es gilt 
$$
f(x)=y
$$

Nun kann für jede beliebig gefahrene Strecke $x$ der Preis $f(x)$ berechnet werden oder umgekehrt.
Der Preis für 5km:
$$ 
f(5) = 2 \cdot 5 + 3 = 13\text{€}
$$   

Wie weit kommt man mit 20 Euro? 
$$ 
20 = 2x + 3 ⇔ x = 8,5[km]
$$

## Übungsaufgaben

### Aufgabe 1
Josef kauft sich für **20000€** einen neuen Benziner. Er weiß aus Erfahrung, dass er **0,23 €/km**   für Tanken und Verschleiß ausgibt.

a) Gib eine Formel an, die nach dem Autokauf die Gesamtkosten in Abhängigkeit der Strecke angibt.

b) Wie weit kommt er mit einem Budget von 25000€?

c) Wie viel Geld wird Josef bis zum Kilometerstand von 100.000km ausgegeben haben?

### Aufgabe 2
Manfred kauft sich für **25000€** einen neuen Diesel. Er weiß aus Erfahrung, dass er **0,19 €/km** für Tanken und Verschleiß ausgibt.

a) Gib eine Formel an, die nach dem Autokauf die Gesamtkosten in Abhängigkeit der Strecke angibt.

b) Wie weit kommt er mit einem Budget von 25000€?

c) Wie viel Geld wird Manfred bis zum Kilometerstand von 100.000km ausgegeben haben?

d) Nach wie vielen Kilometern rentiert sich der Diesel für Manfred verglichen mit dem Benziner von Josef?

### Aufgabe 3
Das Taxiunternehmen Wolf nimmt für eine 1 km lange Fahrtstrecke 50 Cent. 
Dem Fahrgast wird jedoch bereits zu Beginn der Fahrt eine Gebühr von 2,50 € berechnet. 

Stelle dafür eine Funktionsgleichung auf und berechne, wieviel der Fahrgast für 15 km Fahrtstrecke zahlen müsste.

### Aufgabe 4
Ulrich möchte einen neuen Handyvertrag abschließen. Nach langer Recherche stößt er auf zwei Tarife, die für ihn in Frage kommen. Er möchte sein Handy ausschließlich für Telefonie nutzen.

Tarif A: 15 € monatliche Grundgebühr, 2,5 Cent pro angefangener Minute.

Tarif B: 5€ monatliche Grundgebühr, 4 Cent pro angefangener Minute.

a) Stelle die Funktionsgleichungen für beide Tarife auf.

b) Wann lohnt sich für Ulrich welcher Tarif?

c) Ulrich telefoniert pro Monat im Schnitt 400 Minuten. Wieviel zahlt er dabei bei beiden Tarifen?

d) Beschreibe einen Tarif, der folgender Funktionsgleichung entspricht:  
$$ 
h(x) = 0,06x 
$$ 

## Rekonstruktion mit Punkt und Steigung
Wenn die Steigung und ein Punkt einer linearen Funktion bekannt sind, müssen diese Informationen in die **allgemeine Funktionsgleichung** eingesetzt werden, um $b$ zu berechnen. Anschließend werden alle Werte in die Ursprungsform eingesetzt und die vollständige Funktionsgleichung liegt vor.

_Beispiel_

Gegeben sei für eine lineare Funktion die Steigung $m=-2$ und der Punkt $P(-2,2)$.

Die beiden Koordinaten des Punktes $x=-2$ und $y=2$ und die Steigung $m=-2$ werden in die allgemeine Funktionsgleichung eingesetzt und es wird nach $b$ aufgelöst:

Durch Einsetzen von der Steigung m und des berechneten Y-Achsenabschnitts b kann die Funktionsgleichung angegeben werden:

$$
f(x) = -2x-2
$$
 
$$
\begin{array}
&&f(x)&= &mx+b \\ 
⇔&2&= &(-2)⋅(-2)+b \\ 
⇔&2&= &4+b \\
⇔&b&= &-2 \\
\end{array}
$$

Durch Einsetzen von der Steigung $m$ und des berechneten Y-Achsenabschnitts $b$ kann die Funktionsgleichung angegeben werden:
$$
f(x)=-2x-2
$$

## Rekonstruktion mit zwei Punkten
Wenn zwei Punkte einer linearen Funktion bekannt sind, muss zuerst die Steigung $m$ mit dem **Differenzenquotient** ermittelt werden. Der Y-Achsenabschnitt $b$ wird anschließend durch Einsetzen von $m$ und einem Punkt in 
$$
f(x)\ =\ mx+b
$$ 
bestimmt.

_Beispiel_

Gegeben seien die Punkte $P(2,2)$ und $Q(-1,0)$

Die Werte $x_1=2$, $y_1=2$ und $x_2=-1$, $y_2=0$ werden zuerst in die Formel des Differenzenquotient eingesetzt	

$$ 
m = \frac{y_2-y_1}{x_2-x_1}
⇒	m = \frac{0-2}{-1-2} = \frac{-2}{-3} = \frac{2}{3}
$$ 

Ein Punkt (egal welcher von Beiden) wird nun in die Gleichung eingesetzt:

$$
0 = \frac{2}{3}⋅(-1)+b⇔b=\frac{2}{3} 
⇒f(x)\ =\ \frac{2}{3} x+\frac{2}{3}
$$

### Aufgabe 1

Gegeben seien die folgenden Eigenschaften einer linearen Funktion. Bestimme die Funktionsgleichung und zeichne den Graphen in ein Koordinatensystem. 

a) $m=1$ und $P(-2,2)$

b) $m=\frac{1}{3}$ und $P(0,4)$

c) $P(1,2)$ und $Q(4,2)$

d) $P(-4,2)$ und $Q(-6,3)$

### Aufgabe 2

Gegeben sind die folgenden Eigenschaften einer linearen Funktion. Bestimme die Funktionsgleichung und skizziere den Graph in ein Koordinatensystem 

a) $m=\frac{1}{2}$	und	$P(-2,0)$

b) $m=3$	und	$P(-3,1)$

c) $P(1,2)$	und	$Q(4,2)$

d) $P(-4,2)$	und	$Q(-6,3)$ 

### Aufgabe 3
Zeichne die Geraden $y=3x−2$ und $y=−43​x+1$ in ein Koordinatensystem. 
Bestimme die Nullstellen und den Schnittpunkt der Geraden.

### Aufgabe 4
Bestimme den Flächeninhalt des Dreiecks, welches von den Koordinatenachsen und der Gerade $g(x) = 32​x + 5$ eingeschlossen wird.

