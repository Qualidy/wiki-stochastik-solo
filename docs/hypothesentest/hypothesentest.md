# Hypothesentests

Ein Hypothesentest ist ein statistisches Verfahren aus der Interferenzstatistik, mit dem du überprüfst, ob eine Annahme (Hypothese) über eine Datenmenge richtig oder falsch ist.

_Beispiel_
_Stell dir vor, du möchtest wissen, ob ein neues Medikament wirklich wirkt. Du hast eine Gruppe von Patienten, die das Medikament nehmen, und eine Gruppe, die ein Placebo (Scheinmedikament) bekommt. Der Hypothesentest hilft dir herauszufinden, ob der beobachtete Unterschied zwischen den beiden Gruppen zufällig ist oder ob er wirklich auf das Medikament zurückzuführen ist._

## Was sind Hypothesentests?

Die Schritte eines Hypothesentests:
1. Nullhypothese: Dies ist die Ausgangsannahme. Zum Beispiel könnte die Nullhypothese sein: „Das Medikament hat keinen Effekt.“
2. Alternativhypothese: Das ist die Annahme, die du beweisen willst. In unserem Beispiel wäre das: „Das Medikament hat einen Effekt.“
3. Daten sammeln: Du führst ein Experiment durch oder sammelst Daten, um die Hypothesen zu testen.
4. Statistischer Test: Du wählst einen passenden Test, um zu prüfen, wie gut die Daten zur Nullhypothese passen.
5. p-Wert berechnen: Der p-Wert gibt an, wie wahrscheinlich es ist, die beobachteten Daten zu erhalten, wenn die Nullhypothese wahr ist. Ein kleiner p-Wert (meist unter 0,05) bedeutet, dass die Nullhypothese eher falsch ist.
6. Entscheidung: Wenn der p-Wert klein genug ist, lehnst du die Nullhypothese ab und nimmst an, dass die Alternativhypothese stimmt. Wenn der p-Wert groß ist, kannst du die Nullhypothese nicht ablehnen (aber du beweist nicht, dass sie wahr ist).


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

