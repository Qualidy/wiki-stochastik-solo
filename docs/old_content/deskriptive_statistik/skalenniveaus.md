# Skalenniveaus

Das Skalenniveau beschreibt, auf welche Weise Daten gemessen und klassifiziert werden können. 
Es gibt vier Haupttypen von Skalenniveaus, die bestimmen, welche mathematischen Operationen 
und statistischen Analysen auf den Daten möglich sind:

| Skalenniveau    | Operationen                  | Messbare Eigenschaften                                | Beispiel                    |
|-----------------|------------------------------|-------------------------------------------------------|-----------------------------|
| Nominalskala    | $=,\neq$                     | Häufigkeit                                            | Farben, Parteien            |
| Ordinalskala    | $=,\neq,<,>$                 | Häufigkeit, Rangfolge                                 | Schulnoten                  |
| Intervallskala  | $=,\neq,<,>,+,-$             | Häufigkeit, Rangfolge, Abstand                        | Temperatur in Celsius       |
| Verhältnisskala | $=,\neq,<,>,+,-,\times,\div$ | Häufigkeit, Rangfolge, Abstand, natürlicher Nullpuntk | Alter, Temperatur in Kelvin |

``` mermaid
graph TD
    
    S["Neue Datenskala S liegt vor"] --immer-->
    N(["S ist nominalskalliert✅"]) --stelle Frage-->
    OF["Haben die Daten eine Ordnung?"] --Ja-->
    O(["S ist auch ordnialskalliert✅"]) --stelle Frage-->
    IF["Kann man zwei Datenpunkte sinnvoll addieren und erhält einen neuen Datenpunkt?"]--Ja-->
    I(["S ist auch intervallskalliert✅"]) --stelle Frage-->
    VF["Kann jeder Datenpunkt sinnvoll halbiert/verdoppelt werden? Oder: führt verdoppeln immer zu mehr?"] --Ja-->
    V(["S ist auch verhältnisskalliert✅"]) --> 
    F["Fertig"]

    OF--Nein-->F
    IF--Nein-->F
    VF--Nein-->F
```

{{ task(file="tasks/deskriptive_statistik/skalenniveaus_bestimmen.yaml") }} 
