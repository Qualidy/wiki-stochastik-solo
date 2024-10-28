# Das arithmetische Mittel  

Das arithmetische Mittel, oft einfach als Durchschnitt oder Mittelwert bezeichnet, 
ist eine zentrale Kennzahl in der Statistik, welche zu den Lagemaßen zählt. 
Es gibt an, welchen Wert die Daten im Durchschnitt haben. 
Um das arithmetische Mittel zu berechnen, addiert man alle Werte einer Datenreihe und teilt diese 
Summe durch die Anzahl der Werte. 
Es ist eine einfache Methode, um einen typischen Wert der Daten zu bestimmen, 
kann aber durch extreme Ausreißer beeinflusst werden.  

$$ \frac{\text{Summe der Werte}}{\text{Anzahl der Werte}} = \text{Arithmetisches Mittel} $$

!!! formel

    $$ \bar{x} = \frac{1}{n} \sum_{i=1}^n x_i = \frac{1}{n}(x_1 + x_2 + \cdots + x_{n-1} + x_n)$$
    
    - $\bar{x}$ ist das arithmetische Mittel,
    - $n$ ist die Anzahl der Elemente,
    - $x_i$ beschreibt ein einzelnes Element (also $x_1$ das erste, $x_2$ das zweite, $x_n$ das letzte, $x_{n-1}$ das zweitletzte usw.),
    - $i$ ist ein Index, welcher die Elemente durchnummeriert,
    - $\sum_{i=1}^n$ ist das Summenzeichen, mit dem vom Startwert $i$ bis zum Endwert $n$ alle Elemente aufsummiert werden.


???+ beispiel

    Ein Bäcker hat in folgender Tabelle notiert, wie viele Kuchen er in der letzten Woche verkauft hat.
    
    |       | Kuchenverkäufe |
    |-------|----------------|
    | $x_1$ | 4              |
    | $x_2$ | 7              |
    | $x_3$ | 2              |
    | $x_4$ | 3              |
    | $x_5$ | 10             |
    
    Er möchte nun berechnen, wie viele Kuchen er durchschnittlich pro Tag verkauft. Da $5$
    Datenpunkte vorliegen, ist $n=5$.
    
    $$
    \begin{align}
    \bar{x} &= \frac{1}{5}(x_1 + x_2 + x_3 + x_4 + x_5)\\
    &= \frac{1}{5}(4+7+2+3+10)\\
    &= \frac{26}{5}\\
    &= 5{,}2
    \end{align}
    $$

    Das arithmetische Mittel dieses Datensatzes ist also $5{,}2$. 
    Mit anderen Worten verkauft der Bäcker pro Tag durchschnittlich $5{,}2$ Kuchen.

{{ task(file="tasks/deskriptive_statistik/mean_bestimmen.yaml") }}

{{ task(file="tasks/deskriptive_statistik/mean_bestimmen_big.yaml") }}

{{ task(file="tasks/deskriptive_statistik/mean_bestimmen_gruppiert.yaml") }}

!!! excel

    Das Arithmetische Mittel kann in Excel mit Hilfe der Funktion [`MITTELWERT`](https://support.microsoft.com/de-de/office/mittelwert-funktion-047bac88-d466-426c-a32b-8f33eb960cf6). 

    Zusätzlich stehen in Excel die Funktionen [`MITTELWERTWENN`](https://support.microsoft.com/de-de/office/mittelwertwenn-funktion-faec8e2e-0dec-4308-af69-f5576d8ac642)
    und [`MITTELWERTWENNS`](https://support.microsoft.com/de-de/office/mittelwertwenns-funktion-48910c45-1fc0-4389-a028-f7c5c3001690)
    zur Verfügung, um nur ausgewählte Datenpunkte in die Berechnung der Mittelwerte zu beachten. 

    <iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://qualidyschulungen-my.sharepoint.com/personal/viktor_reichert_qualidy_de/_layouts/15/Doc.aspx?sourcedoc={67943b6d-45f9-4b3d-9edf-ec75b26784b7}&action=embedview&AllowTyping=True&ActiveCell='MITTELWERT'!C2&wdDownloadButton=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
