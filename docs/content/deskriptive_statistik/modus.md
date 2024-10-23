# Der Modus

Der Modus ist der Wert in einer Datenreihe, der am häufigsten vorkommt. 
Er zeigt also den häufigsten oder typischsten Wert an. 
Im Gegensatz zum Mittelwert oder Median muss der Modus nicht einmalig sein –
es kann mehrere Modi geben, wenn mehrere Werte gleich oft vorkommen.
Der Modus ist besonders nützlich bei kategorialen Daten, also Daten, 
die in Gruppen eingeteilt sind, wie z. B. die beliebteste Farbe in einer Umfrage.  


<div class="grid cards" markdown>

- _Beispiel Multimodal:_
    
    6 Personen wurden gefragt, welche Automarke sie fahren.
    
    | Automarke |
    |-----------|
    | Audi      |
    | BMW       |
    | Porsche   |
    | Audi      |
    | VW        |
    | BMW       |
    
    Die Modi dieser 6 Menschen sind sowohl "Audi" als auch "BMW". 
    
    Wenn ein Datensatz, so wie dieser mehrere Modi hat, nennt man ihn **multimodal**. 

- _Beispiel Unimodal:_
    
    Den Modus kann man auch von normalen Zahlen bestimmen.
    
    | Schulnote |
    |-----------|
    | 4         |
    | 1         |
    | 3         |
    | 5         |
    | 2         |
    | 1         |
    
    In diesem Fall ist der Modus nur "1".
    
    Wenn ein Datensatz, so wie dieser, nur einen Modus hat, so nennt man ihn **unimodal**. 

</div>


{{ task(file="tasks/deskriptive_statistik/modus_bestimmen.yaml") }}

!!! excel

    In Excel kann die Funktion [`#!excel MODUS.EINF` 
    (Dokumentation)](https://support.microsoft.com/de-de/office/modus-einf-funktion-f1267c16-66c6-4386-959f-8fba5f8bb7f8)
    verwendet werden, um den (kleinsten) Modus zu finden.

    Mit der Funktion  [`MODUS.VIELF` (Dokumentation)](https://support.microsoft.com/de-de/office/modus-vielf-funktion-50fd9464-b2ba-4191-b57a-39446689ae8c)
    gibt ein vertikales Array aller gefundenen Modi zurück.

    ⚠ Achtung: Beide Funktionen ignorieren Text, Wahrheitswerte und leere Zellen! Das Beispiel mit Automarken würde hiermit also
    ohne weiteres gelöst werden können.

    <iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://qualidyschulungen-my.sharepoint.com/personal/viktor_reichert_qualidy_de/_layouts/15/Doc.aspx?sourcedoc={72c3e45b-9538-47e9-981b-f8ccb41dd4b5}&action=embedview&AllowTyping=True&ActiveCell='ein%20Modus'!C2&wdDownloadButton=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
