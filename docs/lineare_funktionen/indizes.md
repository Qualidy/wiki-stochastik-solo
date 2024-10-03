# Indexschreibweise

{{ youtube_video("https://www.youtube.com/embed/H_VSCzHclkw?si=gAH2SWtys7yo3zhe") }}

nach Summenfunktion müssen die einzelnen Summenglieder nicht zwangsläufig einen expliziten Zahlenwert besitzen.
In der folgenden Summe werden die Glieder $a_0$ bis $a_n$ aufsummiert

$$
\sum_{k=0}^{n}a_k = a_1 + a_2 + \cdots + a_n
$$

_Beispiel_

Acht Leute spenden einen anonym einen Geldbetrag. Die Beträge werden als $x$ mit einem Index notiert:

| Spendenbetrag | Wert  |
|---------------|-------|
| $x_1$         | $10$  |
| $x_2$         | $25$  |
| $x_3$         | $5$   |
| $x_4$         | $30$  |
| $x_5$         | $20$  |
| $x_6$         | $80$  |
| $x_7$         | $15$  |
| $x_8$         | $100$ |
 
$$
\sum_{i=1}^{8}x_i = x_1 + x_2 + x_3 + x_4 + x_5 + x_6 + x_7 + x_8 = 285
$$
 
{{ task(file="tasks/lineare_funktionen/index_kleine_geschichte.yaml") }}

{{ task(file="tasks/lineare_funktionen/index_summen.yaml") }}


## Geordnete Indizierung

![](../pictures/geordnete_indizierung.svg)

Wenn wir eine Menge von Daten haben, dann hat der normale Index keine Aussagekraft,
außer vielleicht die Reihenfolge, in der die Daten eingetragen wurden.

Es gibt jedoch eine Schreibweise, mit der man auf das kleinste/größte Element usw. zugreifen kann.
Dazu schreiben wir um den Index eckige Klammern und zeigen so an, welchen Rang das Element hat.

| Indizierung<br/>in Reihenfolge<br/>der Datenerfassung | Inhalt | Indizierung<br/>nach Größe |
|-----------------------------------------------|--------|------------------------|
| $x_1$                                         | 106    | $x_{[7]}$              |
| $x_2$                                         | 30     | $x_{[1]}$              |
| $x_3$                                         | 84     | $x_{[5]}$              |
| $x_4$                                         | 35     | $x_{[4]}$              |
| $x_5$                                         | 30     | $x_{[2]}$              |
| $x_6$                                         | 30     | $x_{[3]}$              |
| $x_7$                                         | 84     | $x_{[6]}$              |

Also $x_{[1]}$ beschreibt das kleinste Element.

$x_{[2]}$ beschreibt das zweit-kleinste Element.

...

$x_{[n]}$ beschreibt das größte Element, wenn wir insgesamt $n$ Datenpunkte haben.

$x_{[n-1]}$ beschreibt das zweitgrößte Element. 

{{ task(file="tasks/lineare_funktionen/geordneter_index_aufgabe_1.yaml") }}

{{ task(file="tasks/lineare_funktionen/geordneter_index_aufgabe_2.yaml") }}

{{ task(file="tasks/lineare_funktionen/geordneter_index_mittleres_element_finden.yaml") }}

