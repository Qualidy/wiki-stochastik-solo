# Hypothesentests

Ein Hypothesentest ist ein statistisches Verfahren aus der Interferenzstatistik, mit dem du überprüfst, ob eine Annahme (Hypothese) über eine Datenmenge richtig oder falsch ist.

_Beispiel_
_Stell dir vor, du möchtest wissen, ob ein neues Medikament wirklich wirkt. Du hast eine Gruppe von Patienten, die das Medikament nehmen, und eine Gruppe, die ein Placebo (Scheinmedikament) bekommt. Der Hypothesentest hilft dir herauszufinden, ob der beobachtete Unterschied zwischen den beiden Gruppen zufällig ist oder ob er wirklich auf das Medikament zurückzuführen ist._

## Was sind Hypothesentests?

Die Schritte eines Hypothesentests:

1. **Nullhypothese**: Dies ist die Ausgangsannahme. Zum Beispiel könnte die Nullhypothese sein: „Das Medikament hat keinen Effekt.“
2. **Alternativhypothese**: Das ist die Annahme, die du beweisen willst. In unserem Beispiel wäre das: „Das Medikament hat einen Effekt.“
3. **Daten sammeln**: Du führst ein Experiment durch oder sammelst Daten, um die Hypothesen zu testen.
4. **Statistischer Test**: Du wählst einen passenden Test, um zu prüfen, wie gut die Daten zur Nullhypothese passen.
5. **p-Wert berechnen**: Der p-Wert gibt an, wie wahrscheinlich es ist, die beobachteten Daten zu erhalten, wenn die Nullhypothese wahr ist. Ein kleiner p-Wert (meist unter 0,05) bedeutet, dass die Nullhypothese eher falsch ist.
6. **Entscheidung**: Wenn der p-Wert klein genug ist, lehnst du die Nullhypothese ab und nimmst an, dass die Alternativhypothese stimmt. Wenn der p-Wert groß ist, kannst du die Nullhypothese nicht ablehnen (aber du beweist nicht, dass sie wahr ist).


## Hypothesen formulieren

Für einen Hypothesentest müssen immer zwei sich **widersprechende** Hypothesen formuliert werden. Das ist zum einen die Nullhypothese $H_0$, welche man widerlegen möchte, und zum anderen die Alternativhypothese $H_1$ (Gegenhypothese), welche man "beweisen" möchte.

_Beispiel_
_Man hat einen sechsseitigen Würfel und möchte herausfinden, ob dieser Würfel "positiv" gezinkt ist, also hohe Zahlen wahrscheinlicher sind als nidriege. Dafür stellt man die Nullhypothese auf, dass der Würfel fair ist oder eher kleine Zahlen wirft ($H_0: \mu \leq 3,5$). Die Alternativhypothese ist dann, dass der Würfel eher hohe Zahlen wirft ($H_1:\mu > 3,5$)._

Anstatt es auf den Erwartungswert zu beziehen, kann man auch den Fokus auf die Wahrscheinlichkeiten legen.

_Beispiel_
_Man hat einen sechsseitigen Würfel und möchte herausfinden, ob dieser Würfel die "6" häufiger würfelt als ein fairer Würfel. Die Alternativhypothese ist dann, dass die Wahrscheinlichkeit eine "6" zu würfeln, höher als $\frac{1}{6}$ ist ($H_0: p > \frac{1}{6}$). Da die Nullhypothese genau das Gegenteil sein muss, muss sie aussagen, dass die Wahrscheinlichkeit eine "6" zu würfeln, gleich oder kleiner als $\frac{1}{6}$ ist ($H_1: p \leq \frac{1}{6}$).

Man unterscheidet beim Hypothesentest zwischen drei unterschiedlichen Herangehenweisen:

- linksseitiger Test, z.B.: $H_0: p \geq 0,5$ und $H_1: p > 0,5$
- rechtsseitiger Test, z.B.: $H_0: p \leq 0,5$ und $H_1: p > 0,5$
- beidseitiger Test, z.B.: $H_0: p = 0,5$ und $H_1: p \neq 0,5$

Was es damit auf sich hat, behandeln wir später.

## Signifikanzniveau und p-Wert

Das Signifikanzniveau (oft als $\alpha$ geschrieben) ist eine Schwelle, die im Hypothesentest festlegt, wie streng du sein willst, wenn du die Nullhypothese ablehnst. Es gibt an, wie groß das Risiko ist, dass du fälschlicherweise die Nullhypothese ablehnst, obwohl sie eigentlich wahr ist. Dies nennt man auch einen Fehler 1. Art. 

_Beispiel_  
_Wir möchten eine Münze untersuchen, von der wir vermuten, dass sie nicht fair ist._

$H_0: p = 0,5$  
$H_1: p \neq 0,5$  

_Wir werfen die Münze nun mehrmals hintereinander. In diesem Fall gucken wir uns an, wie wir damit umgehen, wenn jedes mal Kopf kommt._

$P(K) = 0,5^1 = 0,5$  
$P(K,K) = 0,5^2 = 0,25$  
$P(K,K,K) = 0,5^3 = 0,125$  
$P(K,K,K,K) = 0,5^4 = 0,0625$  
$P(K,K,K,K,K) = 0,5^5 = 0,03125$  

_Ab einem gewissen Punkt, halten wir dann die Chance, dass ein Ereignis eintritt, für zu unwahrscheinlich. Wir glauben dann nicht mehr, dass die Nullhypothese wahr ist und verwerfen diese. Dieser Punkt wird durch das Signifikanzniveau bestimmt._  

Für das Signifikanzniveau wird häufig ein Wert von $\alpha = 0,05$ verwendet. Das ist im Endeffekt eine willkürliche Wahl, welche sich aber historisch eingebürgert hat. Für medizinische Tests wird zum Beispiel oft ein kleinerer Wert für das Signifikanzniveau $\alpha$ verwendet.  

Während das Signifikanzniveau die Schwelle darstellt, ab der wir die Nullhypothese verwerfen, ist der p-Wert die tatsächliche Wahrscheinlichkeit, dass unsere Stichprobe eintritt. Das Signifikanzniveau wird vorher festgelegt, den p-Wert berechnen wir aus unserer Stichprobe. Ist der p-Wert kleiner als das Signifikanzniveau, wird die Nullhypothese abgelehnt.

_Für unser Beispiel könnten wir das klassische Signifikanzniveau von $\alpha = 0,05$ wählen, dann ist die p-Wert von fünfmal Kopf $p = 0,03125$. Da der p-Wert unter unser festgelegten Schwelle liegt, verwerfen wir die Hypothese, dass die Münze fair ist. (Eigentlich würde es sich hier um einen beidseitigen Test handeln, das habe ich zu Anschauungszwecken vernachlässigt.)_


## $\alpha$-Fehler und $\beta$-Fehler

Die Begriffe Alpha-Fehler (Fehler 1. Art) und Beta-Fehler (Fehler 2. Art) beziehen sich auf Fehler, die man bei einem Hypothesentest machen kann, wenn man Entscheidungen über die Nullhypothese trifft.

||$H_0$ ist wahr|$H_0$ ist falsch|
|-|-|-|
|Verwerfe $H_0$| Typ I Fehler ($\alpha$)| kein Fehler|
|Akzeptiere $H_0$|kein Fehler|Typ II Fehler ($\beta$)|

1. Der Alpha-Fehler passiert, wenn du die Nullhypothese ablehnst, obwohl sie in Wirklichkeit wahr ist. Du kommst also zu dem Schluss, dass es einen Effekt oder einen Unterschied gibt, obwohl dies in der Realität nicht der Fall ist.   
   _Beispiel: Du testest, ob ein neues Medikament besser wirkt als ein altes. Wenn du zu dem Schluss kommst, dass das neue Medikament besser ist, obwohl es eigentlich keinen Unterschied gibt, hast du einen Alpha-Fehler gemacht._
2. Der Beta-Fehler passiert, wenn du die Nullhypothese nicht ablehnst, obwohl sie in Wirklichkeit falsch ist. Das bedeutet, du übersiehst einen echten Effekt oder Unterschied.  
   _Beispiel:Du testest wieder das neue Medikament. Diesmal ist es tatsächlich besser als das alte, aber dein Test zeigt keinen Unterschied. Das ist ein Beta-Fehler: Du hast den echten Effekt des neuen Medikaments verpasst._

Der Fokus liegt immer auf dem $\alpha$-Fehler, da dies der "schlimmere" Fehler ist. Hat man zum Beispiel einen Test auf einen tödliche Krankheit, dann soll der Fehler, dass ein Patient die Krankheit hat und der Test es nicht erkennt, möglichst klein sein. Im Gegensatz dazu kann es auch passieren, dass der Test ergibt: ein Patient hat die Krankheit, obwohl er eigentlich gesund ist. Das würde man als $\beta$-Fehler bezeichnen und wäre weniger "schlimm". Die Wahrscheinlichkeiten für den Fehler 1. Art hat als Symbol $\alpha$, die Wahrscheinlichkeit für den Fehler 2. Art hat als Symbol $\beta$.

Natürlich möchte man eigentlich keine Fehler machen. Je kleiner man aber den $\alpha$-Fehler wählt, desto größer wird dann der $\beta$-Fehler. Umgekeht gilt das gleiche, wenn wir unseren $\beta$-Fehler kleiner machen, dann wächst der $\alpha$-Fehler. Die einzige Möglichkeit, beide Fehler kleiner zu machen, besteht darin, die Stichprobengröße zu erhöhen.

## links-, rechts- und beidseitiger Test

In einem Hypothesentest gibt es drei Arten von Tests, je nachdem, wie die Alternativhypothese formuliert ist: linksseitig, rechtsseitig oder beidseitig. Der Unterschied liegt darin, auf welche Richtung des Unterschieds oder Effekts wir testen:

1. Linksseitiger Test:
   Hier vermuten wir, dass der tatsächliche Wert kleiner ist als ein bestimmter Wert. Die Alternativhypothese (H₁) besagt also, dass der Unterschied auf der linken Seite liegt.
   Beispiel: „Die durchschnittliche Temperatur ist niedriger als 20°C.“
2. Rechtsseitiger Test:
   In diesem Fall vermuten wir, dass der tatsächliche Wert größer ist als ein bestimmter Wert. Die Alternativhypothese (H₁) zeigt einen Unterschied auf der rechten Seite.
   Beispiel: „Die durchschnittliche Temperatur ist höher als 20°C.“
3. Beidseitiger Test:
   Hier interessiert uns, ob der tatsächliche Wert entweder größer oder kleiner als der angenommene Wert ist, aber ohne festzulegen, in welche Richtung. Die Alternativhypothese testet also auf beide Seiten.
   Beispiel: „Die durchschnittliche Temperatur ist ungleich 20°C.“ (kann höher oder niedriger sein)

## Durchführung eines Hypothesentests

### Hypothesentest mit diskreter Zufallsgröße

Anhand eines Beispiels führen wir einen kompletten Hypothesentest durch.

Eine Firma produziert in zwei Fabriken Prozessoren, von denen aber ein gewisser Anteil defekt ist. In Fabrik A ist der Anteil der defekten Prozessoren 10%. In Fabrik B ist der Anteil der defekten Prozessoren 20% und es werden insgesamt mehr Prozessoren als in Fabrik A pro Tag hergestellt. In einer Halle der Firma werden Pakete mit je 10.000 Prozessoren gelagert. Ein Paket ist in der Lagerhalle aufgetaucht auf dem die Beschriftung fehlt, aus welcher Fabrik das Paket stammt. Eine Stichprobe von 100 Prozessoren aus dem Paket hat ergeben, dass 16 Prozessoren defekt sind. Du sollst nun beurteilen, aus welcher Fabrik das Paket stammt. 

Da Fabrik B mehr produziert, liegt die Vermutung nahe, dass das Paket aus Fabrik B stammt. Wir wählen daher, "Paket stammt nicht aus Fabrik A" als Alternativhypothese aus. Damit ist die Nullhypothese "Paket stammt aus Fabrik A".  
Wir führen einen rechtsseitigen Test durch, weil wir nur prüfen, ob eine größere Defektrate als 10% wahrscheinlich ist.  

$$ H_0: p \leq 0,1 $$

$$ H_1: p > 0,1 $$

$$ \alpha = 0,05 $$

Ein Prozessor kann entweder defekt oder funktionsfähig sein, damit handelt es sich also um eine binomialverteilte Zufallsgröße. 

Formel aus der Binomialverteilung:

$$ P(X=k) = \binom{n}{k} \cdot p^k \cdot (1-p)^{n-k} $$

Wir müssen nun berechnen, was die Wahrscheinlichkeit ist 16 oder mehr defekte Prozessoren bei einer Rate von 10% zu haben.

$$ P(X \geq 16) = 1 - P(X \leq 15) $$

$$ P(X \leq 15) = \sum_{i=0}^{15} \binom{100}{i} \cdot 0,1^i \cdot (1-0,1)^{100-i} \approx 0,96 $$

$$ P(X \geq 16) \approx 1 - 0,96 = 0,04 $$

Es gibt also nur eine 4-prozentige Chance, dass das Paket tatsächlich aus Fabrik A stammt, wenn 16 defekte Prozessoren in der Stichprobe sind. Diese 4% liegt unterhalb unseres Signifikanzniveaus von 5%. Das Ergebnis halten wir also für zu unwahrscheinlich für Fabrik A, weswegen wir die Nullhypothese ablehnen und davon ausgehen, dass das Paket aus Fabrik B stammt.


### Hypothesentest mit stetiger Zufallsgröße

Eine Population von Riesen hatte vor 10 Jahren eine durchschnittliche Körpergröße von 3 Metern mit einer Standardabweichung von 0,5 Metern. Nun soll getestet werden, ob sich die durschnittliche Körpergröße verändert hat. Dafür wird eine Stichprobe von 100 Riesen genommen und ein Signifikanzniveau von 4% festgelegt. Bei der Stichprobe ergibt sich eine durchschnittliche Körpergröße von 2,9 Metern.

Als Alternativhypothese wählen wir also, dass sich die durchschnittliche Körpergröße verändert hat. Entsprechend ist die Nullhypothese, dass sich die durchschnittliche Körpergröße nicht verändert hat.  
Wir führen einen beidseitigen Test durch, weil wir gleichzeitig prüfen wollen, ob sich der Durchschnitt nach oben oder unten verändert hat.

$$ H_0: \mu = 3 $$

$$ H_1: \mu \neq 3 $$

$$ \alpha = 0,04 $$

Durch den zentralen Grenzwertsatz wissen wir, dass die Mittelwerte der Stichproben normalverteilt um den Mittelwert der Gesamtpopulation liegen. Wir können aus der Standardabweichung der Gesamtpopulation die Standardabweichung der Stichproben berechnen.

$$ \mu_s = 3 $$

$$ \sigma_s = \frac{\sigma_0}{\sqrt{n}} = \frac{0,5}{10} = 0,05 $$

Nun müssen wir den passenden z-Wert für den Mittelwert der Stichprobe berechnen.

$$ z = \frac{x - \mu_s}{\sigma_s} = \frac{2,9 - 3}{0,05} = -2 $$

Aus der z-Werte-Tabelle können wir für $z=2$ einen Wert von $0,9772$ ablesen. Da wir es mit einem negativen z-Wert zu tun haben, müssen wir diesen Wert jetzt noch von $1$ abziehen $1-0,9772 = 0,0228$. Dieser Wert sagt jetzt also aus, dass die Wahrscheinlichkeit bei einer Stichprobe den Mittelwert von $2,9$ oder weniger zu erhalten, ungefähr 2,3 % ist, wenn sich der Mittelwert von vor 10 Jahren nicht verändert hat.  
Diese 2,3% liegen natürlich unterhalb der 4%, die wir als Signifikanzniveau festgelegt haben. Da wir aber auf eine Abweichungen nach oben und unten testen, müssen wir auch unser Signifikanzniveau gleichmäßig auf beide Seiten verteilen. Das heißt also wir müssen hier die 2,3% mit 2% vergleichen. Wir sehen also, dass unser berechneter Wert nicht ganz unser Signifikanzniveau unterschreitet. Deswegen können wir unsere Nullhypothese hier nicht verwerfen und nehmen dann also weiter an, dass sie gilt.


## Konfidenzintervall

Ein Konfidenzintervall ist ein Bereich, der eine Schätzung dafür angibt, wo der wahre Wert einer unbekannten Größe (zum Beispiel der Mittelwert einer Population) mit einer bestimmten Wahrscheinlichkeit liegt.

_Beispiel_  
_Stell dir vor, du machst eine Umfrage, um den durchschnittlichen Fernsehkonsum in einer Stadt herauszufinden. Da jeden einzelnen Bürger zu befragen, zu lange dauert, nimmst du nur eine Stichprobe. Der Mittelwert deiner Stichprobe ist eine Schätzung des wahren Mittelwerts für die ganze Stadt, er könnte also von der Realität abweichen. Das Konfidenzintervall gibt dir einen Bereich an, in dem der wahre Mittelwert mit hoher Wahrscheinlichkeit liegt._

_Beispiel_  
_Es sind Wahlen. Wir möchten herausfinden, wie hoch die Wahrscheinlichkeit, dass ein zufällig ausgewählter Mensch Partei "X" gewählt hat. Dafür nehmen wir eine Stichprobe von 100 Menschen. Von diesen 100 Menschen haben 42 Partei "X" gewählt. Die Wahrscheinlichkeit Partei "X" zu wählen, ist für Menschen dieser Stichprobe also 42% ($p_s = 0,42$). Durch den zentraler Grenzwertsatz wissen wir, dass die Wahrscheinlichkeit der Stichprobe nah an der Realität liegt._

Formeln des zentralen Grenzwertsatzes:

$$ \mu_s = \mu $$

$$ \sigma_s = \frac{\sigma}{\sqrt{n}} $$ 

_Für den Erwartungswert $\mu$ können wir also $p_s = 0,42$ übernehmen. Nun wollen wir noch die Standardabweichung der Stichprobe $\sigma_s$ berechenen. Wir kennen nicht die Standardabweichung der Grundgesamtheit, aber wir wissen, dass dieser Versuch bernoulliverteilt ist. (Entweder wählt ein Mensch Partei "X": Erfolg, oder eben nicht: Misserfolg). Die Standardabweichung einer Bernoulliverteilung können wir berechnen._

$$ \sigma_s = \frac{\sigma}{\sqrt{n}} = \frac{\sqrt{p \cdot (1-p)}}{\sqrt{n}} $$ 

_Dafür bräuchte man jetzt den Wert $p$. Wir kennen aber nur $p_s$ , da dieser Wert laut des zentralen Grenzwertsatzes auch ungefähr $p$ sein müsste, nehmen wir hier $p_s$._

$$ \sigma_s = \frac{\sqrt{p_s \cdot (1-p_s)}}{\sqrt{n}} = \frac{\sqrt{0,42 \cdot (1-0,42)}}{\sqrt{100}} \approx 0,05 $$

_Nun haben wir den Mittelwert, die Standardabweichung und wir wissen über die 68-95-99-Regel, dass ungefähr 95% der Mittelwerte der Stichproben in einem Bereich von zwei Standardabweichungen um den Mittelwert der Grundgesamtheit liegen._

$$ p_{obere\ Grenze} = p_s + 2 \sigma_s \approx 0,42 + 0,1 = 0,52 $$

$$ p_{untere\ Grenze} = p_s - 2 \sigma_s \approx 0,42 - 0,1 = 0,32 $$

_Damit haben wir das Konfidenzintervall $[0,32 ; 0,52]$ bestimmt. Mit einer 95-prozentigen Wahrscheinlichkeit, liegt der wahre Mittelwert in diesem Bereich._  

Das Konfidenzintervall können wir mit der Stichprobengröße $n$ beeinflussen. Ein größeres $n$ führt zu einem kleineren Konfidenzintervall.

$$ \sigma_s =  \frac{\sqrt{0,42 \cdot (1-0,42)}}{\sqrt{10000}} \approx 0,005 $$

$$ p_{obere\ Grenze} = p_s + 2 \sigma_s \approx 0,42 + 0,01 = 0,43 $$

$$ p_{untere\ Grenze} = p_s - 2 \sigma_s \approx 0,42 - 0,01 = 0,41 $$

_Hätten wir beim vorherigen Beispiel mit einer Stichprobe von 10.000 ($n = 10000$) Menschen gearbeitet, dann wäre unser Konfidenzintervall deutlich kleiner $[0,41 ; 0,43]$._

 