## Das arithmetische Mittel  
Das arithmetische Mittel, oft einfach als Durchschnitt oder Mittelwert bezeichnet, ist eine zentrale Kennzahl in der Statistik, welche zu den Lagemaßen zählt. Es gibt an, welchen Wert die Daten im Durchschnitt haben. Um das arithmetische Mittel zu berechnen, addiert man alle Werte einer Datenreihe und teilt diese Summe durch die Anzahl der Werte. Es ist eine einfache Methode, um einen typischen Wert der Daten zu bestimmen, kann aber durch extreme Ausreißer beeinflusst werden.  

$$ \frac{Summe\ der\ Werte}{Anzahl\ der\ Werte} = Arithmetisches\ Mittel $$  

_Beispiel_
Ein Bäcker hat in folgender Tabelle notiert, wie viele Kuchen er in der letzten Woche verkauft hat.

|Kuchenverkäufe|
|-|
|4|
|7|
|2|
|3|
|10|

Er möchte nun berechnen, wie viele Kuchen er durchschnittlich pro Tag verkauft.

$$ \frac{4+7+2+3+10}{5} = 5,2 $$

Das arithmetische Mittel dieses Datensatzes ist also 5,2. Mit anderen Worten verkauft der Bäcker pro Tag durchschnittlich 5,2 Kuchen.

_Mathematische Schreibweise_

$$ \bar{x} = \frac{1}{n} \sum_{i=1}^n x_i $$

- $\bar{x}$ ist das arithmetische Mittel
- $n$ ist die Anzahl der Elemente
- $x_i$ beschreibt ein einzelnes Element
- $i$ ist ein Index, welcher die Elemente durchnummeriert
- $\sum_{i=1}^n$ ist das Summenzeichen, mit dem vom Startwert $i$ bis zum Endwert $n$ alle Elemente aufsummiert werden

{{ task(file="tasks/deskriptive_statistik/mean_bestimmen.yaml") }}

{{ task(file="tasks/deskriptive_statistik/mean_bestimmen_big.yaml") }}

{{ task(file="tasks/deskriptive_statistik/mean_bestimmen_gruppiert.yaml") }}