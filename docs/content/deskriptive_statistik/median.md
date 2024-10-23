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

!!! excel

    In Excel kann der Median mit der Funktion [`MEDIAN`](https://support.microsoft.com/de-de/office/median-funktion-d0916313-4753-414c-8537-ce85bdd967d2)
    bestimmt werden. 

    ⚠ Achtung: Die Funktion ignoriert Text, Wahrheitswerte und leere Zellen!

    <iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://qualidyschulungen-my.sharepoint.com/personal/viktor_reichert_qualidy_de/_layouts/15/Doc.aspx?sourcedoc={f0e82fa7-fcb9-4a73-a4b0-e2a6fb4cd308}&action=embedview&AllowTyping=True&ActiveCell='MEDIAN'!C2&wdDownloadButton=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
