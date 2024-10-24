# Der Median
Der Median ist ein Maß für die zentrale Tendenz einer Datenmenge. 
Er ist der Wert, der die Daten in zwei gleich große Hälften teilt: 50 % der Werte liegen unterhalb 
des Medians und 50 % darüber. Um den Median zu finden, sortiert man die Daten der Größe nach. 
Bei einer ungeraden Anzahl von Werten ist der Median der mittlere Wert, bei einer geraden Anzahl 
nimmt man den Durchschnitt der beiden mittleren Werte. Der Median ist weniger anfällig für 
Ausreißer als der Durchschnitt (arithmetisches Mittel).  

<div class="grid cards" markdown>

-   _Beispiel mit ungerader Anzahl an Werten_  
    
    ---

    |Kuchenverkäufe|
    |-|
    |4|
    |7|
    |2|
    |3|
    |10|
    
    Nachdem man die Werte sortiert, erhält man folgende Tabelle.  
    
    |Kuchenverkäufe|
    |-|
    |2|
    |3|
    |4|
    |7|
    |10|

    So lässt sich der Median sehr leicht ablesen. In diesem Fall ist es die 4, da genau zwei Werte größer und 
    zwei Werte kleiner als die 4 sind.  

-   _Beispiel mit gerader Anzahl an Werten:_
    
    ---

    |Kuchenverkäufe|
    |-|
    |2|
    |3|
    |4|
    |5|
    |7|
    |10|
    
    In diesem Beispiel sind sowohl $4$ als auch $5$ gleich mittig. 
    Um hier den Median zu bestimmen, berechnen wir den Durchschnitt beider Werte.  

    $$ \frac{4+5}{2} = 4,5 $$
    
    Damit ist der Median in diesem Fall $4,5$.

</div>

{{ task(file="tasks/deskriptive_statistik/median_bestimmen.yaml") }}

Mathematisch drückt man den Median wie folgt aus:

Sei $x$ ein ordinal skaliertes Merkmal mit $n$ Elementen. Der Modus wird $\bar{x}_{mod}$ genannt und wird
wie folgt berechnet:

<div class="grid" markdown>
<div markdown>
Wenn $n$ ungerade ist:

$$
\bar{x}_{mod} = x_{[\frac{n+1}{2}]}
$$
</div>
<div markdown>

Wenn $n$ gerade ist:

$$
\bar{x}_{mod} = \frac{1}{2} \cdot \left( x_{[\frac{n}{2}]} + x_{[\frac{n}{2}+1]} \right)
$$
</div>
</div>

Schauen wir uns noch einmal die letzten beiden Beispiele an, um uns klar zu machen,
wie man die Formel liest:

<div class="grid cards" markdown>

-   _Beispiel mit ungerader Anzahl an Werten_  
    
    ---
    
    Zunächst liegt der Datensatz unsortiert vor:    

    | normaler Index | Kuchenverkäufe |
    |----------------|----------------|
    | $x_1$          | 4              |
    | $x_2$          | 7              |
    | $x_3$          | 2              |
    | $x_4$          | 3              |
    | $x_5$          | 10             |
    
    Nachdem man die Werte sortiert, erhält man folgende Tabelle.  
    
    | sortierter Index | Kuchenverkäufe | normaler Index |
    |------------------|----------------|----------------|
    | $x_{[1]}$        | 2              | $x_3$          |
    | $x_{[2]}$        | 3              | $x_4$          |
    | $x_{[3]}$        | 4              | $x_1$          |
    | $x_{[4]}$        | 7              | $x_2$          |
    | $x_{[5]}$        | 10             | $x_5$          |

    Wir haben $5$ Werte. **Also ist $n=5$**.

    Da $5$ **ungerade** ist, kannst du diese in die Formel für ungerade $n$ einsetzen:

    $$ 
    \bar{x}_{mod} = x_{[\frac{n+1}{2}]} = x_{[\frac{5+1}{2}]} = x_{[\frac{6}{2}]} = x_{[3]} = x_1 = 4
    $$

-   _Beispiel mit gerader Anzahl an Werten:_
    
    ---

    | sortierter Index | Kuchenverkäufe |
    |------------------|----------------|
    | $x_{[1]}$        | 2              |
    | $x_{[2]}$        | 3              |
    | $x_{[3]}$        | 4              |
    | $x_{[4]}$        | 5              |
    | $x_{[5]}$        | 7              |
    | $x_{[6]}$        | 10             |
    
    In diesem Beispiel liegen $6$ Werte vor. **Also ist $n=6$**.

    Da $6$ **gerade** ist, kannst du dies in die Formel für gerade $n$ einsetzen:

    $$
    \begin{align}
    \bar{x}_{mod} & = \frac{1}{2} \cdot \left( x_{[\frac{n}{2}]} + x_{[\frac{n}{2}+1]} \right) \\
    & = \frac{1}{2} \cdot \left( x_{[\frac{6}{2}]} + x_{[\frac{6}{2}+1]} \right) \\
    & = \frac{1}{2} \cdot \left( x_{[3]} + x_{[4]} \right) \\
    & = \frac{1}{2} \cdot \left( 4 + 5 \right) \\
    & = 4,5
    \end{align}
    $$
</div>

{{ task(file="tasks/deskriptive_statistik/median_bestimmen_formel.yaml") }}

{{ task(file="tasks/deskriptive_statistik/median_bestimmen_fallunterscheidung.yaml") }}



!!! excel

    In Excel kann der Median mit der Funktion [`MEDIAN`](https://support.microsoft.com/de-de/office/median-funktion-d0916313-4753-414c-8537-ce85bdd967d2)
    bestimmt werden. 

    ⚠ Achtung: Die Funktion ignoriert Text, Wahrheitswerte und leere Zellen!

    <iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://qualidyschulungen-my.sharepoint.com/personal/viktor_reichert_qualidy_de/_layouts/15/Doc.aspx?sourcedoc={f0e82fa7-fcb9-4a73-a4b0-e2a6fb4cd308}&action=embedview&AllowTyping=True&ActiveCell='MEDIAN'!C2&wdDownloadButton=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
