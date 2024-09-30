# Mengenlehre

Unter einer Menge versteht man in der Mathematik jede Zusammenfassung von verschiedenen Objekten zu einer Gesamtheit.
Es gibt verschiedene Darstellungen, wie Mengen zusammengefasst werden können. 

*	Aufzählende Schreibweise
*	Beschreibende Schreibeweise
*	Intervalle

## Aufzählende Schreibweise

In der aufzählenden Schreibweise werden die einzelnen Elemente der Menge durch Kommas voneinander getrennt und zwischen zwei geschweiften Klammern aufgezählt.

_Beispiel_ 

$$
\begin{align*}
A &= \{1, 2, 3\} \\
B &= \{-4, -3, -2, -1, 0, 1, 2, 3, 4\} \\
C &= \{1, \dots, 49\}
\end{align*}
$$

## Beschreibende Schreibweise
In der beschreibenden Schreibweise wird zunächst eine Variable aus einer bekannten Menge eingeführt. Nach dem Trennstrich in der Mitte wird die Menge durch die Variable präziser eingegrenzt. Mehrere Eingrenzungen werden mit dem logischen “und” bzw. “oder” verknüpft.

_Beispiel_

$$
\begin{align*}
A &= \{x∈N│x≤3\} \\
B &= \{x∈Z│-4≤x≤4\} \\
C &= \{x∈N│x≤49\}
\end{align*}
$$

## Aufgabe
Gegeben ist jeweils entweder die aufzählende oder die beschreibende Schreibweise. Forme die gegebene Menge in die jeweils andere Schreibweise um

{{ task(file="tasks/mengenlehre/beschreibende_und_aufzaehlende_schreibweise.yaml") }}

## Intervall-Schreibweise
Wenn über reelle Zahlen gesprochen wird, sind alle Zahlen auf dem Zahlenstrahl gemeint. Eine Aufzählung wäre hier deshalb unsinnig. Es können bestimmte Bereiche des Zahlenstrahls mit Hilfe der Intervall-Schreibweise dargestellt werden. Für Intervalle werden unterschiedliche Klammern verwendet. Wenn der Randwert zur Menge gehört, dann wird eine eckige Klammer […] verwendet, wenn der Randwert ausgeschlossen wird, dann wird eine runde Klammer (…) verwendet.

_Beispiele_

| Beispiel | Bezeichnung | Erklärung |
|-------|-------------------------|------------------------------------------|
| **[2,9]** | geschlossenes Intervall | Alle Werte von **2** bis **9**, inklusive **2** und **9**|
|**(2,9)** | offenes Intervall       | Alle Werte von **2** bis **9**, exklusive **2** und **9**|
|**(2,9]**  | halboffenes Intervall   | Alle Werte von **2** bis **9**, exklusive **2** bzw. inklusive **9**|
|**[2,9)**  | halboffenes Intervall   | Alle Werte von **2** bis **9**, inklusive **2** bzw. exklusive **9**|

{{ task(file="tasks/mengenlehre/menge_zu_intervall.yaml") }} 
 
{{ task(file="tasks/mengenlehre/intervall_in_beschreibende.yaml") }} 

{{ task(file="tasks/mengenlehre/beschreibende_in_intervall.yaml") }} 
