# ANOVA

ANOVA (Analysis of Variance) steht für Analyse der Varianz und ist ein statistisches Verfahren, das verwendet wird, um zu testen, ob es signifikante Unterschiede zwischen den Mittelwerten von mehreren Gruppen gibt.

_Beispiel_  
_Angenommen, du möchtest untersuchen, ob der durchschnittliche Umsatz in drei verschiedenen Filialen unterschiedlich ist. Mit ANOVA kannst du testen, ob die Unterschiede im Umsatz zwischen den Filialen auf echten Unterschieden beruhen oder ob sie durch Zufall entstanden sind._

Beim ANOVA bedienen wir uns des sogenannten F-Tests, bei dem das Verhältnis der Varianz zwischen den Gruppen zur Varianz innerhalb der Gruppen gemessen wird.  
Genau wie bei den Hypothesentest formulieren wir Null- und Alternativhypothesen.

## Einfaktorielles ANOVA

Die Einfaktorielle ANOVA (one-way ANOVA) ist eine spezielle Form der ANOVA, die verwendet wird, um zu testen, ob es signifikante Unterschiede zwischen den Mittelwerten von mehr als zwei Gruppen gibt, wobei nur ein Faktor (eine unabhängige Variable) betrachtet wird.

_Beispiel_  
_Angenommen, du untersuchst den Einfluss von drei verschiedenen Lernmethoden auf die Noten von Schülern. Hier ist die Lernmethode der eine Faktor, der in drei Gruppen (Methoden) unterteilt ist. Das einfaktorielle ANOVA prüft, ob die Noten der Schüler zwischen den drei Gruppen signifikant unterschiedlich sind._  

_Es wird eine Stichprobe aus allen drei Gruppen gezogen, welche misst, wie viele Themen jemand aus der Gruppe pro Woche lernt._

|Buchlerner|Vorlesungslerner|Videolerner|
|-|-|-|
|6|7|7|
|7|8|9|
|8|9|11|

_Nullhypothese: die Mittelwerte der Gruppen sind gleich: alle lernen gleich effektiv $H_0: \mu_1 = \mu_2 = \mu_3$._

_Alternativhypothese: die Mittelwerte der Gruppen unterscheiden sich: die Gruppe lernen unterschiedlich effektiv $H_1: \mu_1 \neq \mu_2 \neq \mu_3$._

- Berechne die Mittelwerte jeder Stichprobe.

$$ \mu_{s1} = \frac{6+7+8}{3} = 7 $$

$$ \mu_{s2} = \frac{7+8+9}{3} = 8 $$

$$ \mu_{s3} = \frac{7+9+11}{3} = 9 $$

- Berechne den Mittelwert der Stichprobenmittelwerte, bzw. den Mittelwert aller 9 Datenpunkte.

$$ \mu_{gesamt} = \frac{7+8+9}{3} = 8 $$

- Berechne jede Differenz zwischen Mittelwert einer Stichprobe und Gesamtmittelwert, bilde das Quadrat der Differenz, multipliziere das Quadrat mit der Anzahl der Datenpunkte pro Stichprobe und bilde schließlich die Summe dieser drei Werte.

$$ SSC = \sum_{i=1}^m n(\mu_i - \mu_{ges})^2 = 3(7-8)^2 + 3(8-8)^2 + 3(9-8)^2 = 6 $$

Diese Summe ist der erste wichtige Wert, den wir uns merken müssen. Wir nennen ihn SSC (sum of squares (columns)).

Als nächstes berechnen wir die Varianzen innerhalb der Gruppen.

|$\sum (x_{1i}-\mu_{s1})^2$|$\sum (x_{2i}-\mu_{s2})^2$|$\sum (x_{3i}-\mu_{s3})^2$|
|-|-|-|
|$(6-7)^2 = 1$|$(7-8)^2 = 1$|$(7-9)^2 = 4$|
|$(7-7)^2 = 0$|$(8-8)^2 = 0$|$(9-9)^2 = 0$|
|$(8-7)^2 = 1$|$(9-8)^2 = 1$|$(11-9)^2 = 4$|
|$\sum = 2$|$\sum = 2$|$\sum = 8$|

Die drei Varianzen summieren wir auf. Das ist der zweite wichtige Wert für ANOVA mit dem Namen SSE (sum of squares (errors)).

$$ SSE = 2+2+8 = 12 $$

SSC und SSE müssen wir nun durch ihre entsprechenden Freiheitsgrade teilen, um zum MSC (mean sum of squares (columns)) und zum MSE (mean sum of squares (errors)) zu gelangen, mit denen wir das sogenannte "f-ratio" berechnen können.

Die Freiheitsgerade 

