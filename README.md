# A guide through my projects and GitHub repositorys

<!--START_SECTION:waka-->
<!--END_SECTION:waka-->

(This page will be hopefully translated to english some day.)

Hier möchte ich eine kleine (unvollständige) Übersicht zu allem Möglichen, das ich so mache, erstellen. Mittlerweile verliere ich nämlich langsam selbst manchmal den Überblick über alle GitHub-repositorys, sodass das langsam mal an der Zeit ist. Außerdem möchte ich auch gerne Links und Projekte weitergeben, die ich für cool und/oder hilfreich befinde.

Falls jemand etwas interessant findet und/oder mehr Informationen haben möchte, macht gerne ein Issue auf oder schreibt eine Mail.

## Lehre

### Programmierkurs Julia (FSS 2023)

Siehe [hier](https://github.com/JohannesNaegele/Programmierkurs-Julia).

### Stochastik I (HWS 2021)

Immerhin hab ich hier wenn schon nicht mega viel inhaltlich, dann doch wenigstens gestalterisch einiges beigesteuert (Videoschnitt, Grafiken, etc.). Die Vorlesung ist cool; jedem der Interesse an einer sauberen maßtheoretischen Einführung in die Stochastik hat, kann ich sie nur empfehlen.

YouTube-Playlist: https://youtube.com/playlist?list=PLy5qRKPWp6SBwfc1kn-b66cWc84cOgvqZ

Website: https://www.wim.uni-mannheim.de/doering/teaching/hws21/stochastik-1/

## Data science

### Degustation

To be explained.


## LaTeX und Publishing

## Beamer templates (2020)

https://github.com/JohannesNaegele/Beamer/blob/master/Template.pdf

Oder confidential.

### Interaktive Dokumente (2020)

Siehe https://github.com/JohannesNaegele/pdf.js-precompiled

In der Vergangenheit habe ich mich an ein paar ziemlich abgespaceten (und extrem unnötigen :D) LaTeX-Projekten versucht. Grundsätzlich hat mich immer extrem genervt, dass ich zwar statische Dokumente in LaTeX super erstellen konnte, sobald es aber mit interaktiven Elementen (z. B. Videos, Animationen, ...) sein sollte (wie etwa bei [desmos](https://learn.desmos.com/sliders) oder [GeoGebra](https://www.geogebra.org)), war das die reinste Katastrophe. Das liegt insbesondere daran, dass das PDF-Format für sich hier erhebliche Mängel mitbringt. In der Theorie ist dort nämlich einiges möglich, in der Praxis ist das aber meistens Mist, weil das dann über Adobe Flash und Shockwave etc. funktioniert. Wir erinnern uns: Bitte nicht das! In der Konsequenz funktioniert das dann (wenn überhaupt) nur mit dem Adobe PDF-Reader und nicht auf mobilen Geräten. Sprich: Man macht sich eine Riesenarbeit, nur dass das dann nachher bei der Hälfte der Leser gar nicht ankommt.

Grundsätzlich kommt aber bei LaTeX noch ein weiteres Problem dazu: Was man haben wollen würde, ist ein Dokument, dass zur Runtime gesetzt wird und somit Animationen *beim Abspielen* generiert werden. Das Problem ist nur: Weil LaTeX sequentiell arbeitet und kleine Änderungen im Code weitreichende Umformatierungen zur Folge haben können, müsste dann jedesmal *das komplette Dokument* neu gesetzt werden. Wenn man aber für 25 Frames/s jedes Mal das Dokument neu generieren muss, ist das offensichtlich Quark. 

Was also tun? Interessanterweise gibt es hier sehr unterschiedliche Ansätze, die alle ziemlich unterschiedlich aussehen:

1.  Man ignoriert die Probleme und arbeitet weiter mit einem PDF und mit Pseudointeraktivität
2.  Man baut einen PDF-Website-Hybrid
3.  Man eskaliert komplett und geht auf low-level TeX-Ebene

#### 1. Generische PDF-Lösung

Was zur Hölle meine ich mit *Pseudointeraktivität*? Der Punkt ist: Wenn ich nicht zur Runtime rendern kann, dann muss ich "interaktive" Elemente eben vorkompilieren. D. h.: Angenommen, ich habe eine Grafik mit Slidern (Schiebereglern) für *n* verschiedene Parameter (z. B. eine Normalverteilungskurve mit μ und σ²), dann mache ich halt ein Gitter mit *n* Dimensionen und diskretisiere das Ganze. Am Ende habe ich dann z. B. 10 mögliche Werte für μ und 1000 mögliche Werte für σ². Für ein hinreichend feines Gitter bietet das also volle Funktionalität (abgesehen von sehr fortgeschrittenen Anwendungen). Am Ende macht man also einfach einen Film, bei dem jedes Frame einem bestimmen Punkt in der Animation entspricht und von dieser angesteuert werden kann. Hier kommt theoretisch noch ein Link hin, wo das dann demonstriert wird. Problematisch ist dabei aber, dass der Speicherbedarf natürlich mit der Anzahl der Möglichkeiten explodiert. Und niemand möchte ein Uniskript mit 1 GB Größe.

Konkret bindet man dann bei Möglichkeit 1. den Slider (oder was auch immer) extern über das [media9](https://ctan.org/pkg/media9)-Package als .swf (Shockwave) ein. Diesen wiederum erstellt man in Adobe Flex mit einer mxml-Datei (Abfuck). Und die Animation macht man dann in LaTeX mit dem [animate](https://ctan.org/pkg/animate)-Package. Das heißt: Ich sage dem animate-Package: Generiere mir bitte 200 Frames, wobei du mir diesen counter hier erhöhst. Ich gehe dann her und bastele eine Bijektion von dem counter in meine verschiedenen Parameter, sodass also im vorigen Beispiel 10000 Frames allen Kombinationen von den 10 μ und 1000 σ² zugeordnet werden. Die Grafik selbst kann dann von einem beliebigen Package generiert werden, ich verwende immer [TikZ](https://www.ctan.org/pkg/pgf).

#### 2. Hybrid-Lösung

Dieser Ansatz ermöglicht vor allem, dass das Dokument mit mehr Systemen kompatibel ist. Die Idee ist, dass man sich einfach das beste aus den zwei Welten Website und PDF zusammenbastelt: Eigentlich bietet eine Website ja genau die Interaktivität, die man will, nur leider sieht sie dafür auf verschiedenen Geräten unterschiedlich aus; feine Typografie ist quasi unmöglich. Natürlich könnte man anstelle einer Website auch eine GUI-Applikation mit dem PDF verbinden, das ist allerdings weniger universell und bietet kaum Mehrwert (bis auf Offlinefunktionalität, dazu komme ich noch).

...Rest fehlt noch

#### 3. TeX-Lösung
...ausführliche Beschreibung kommt auch noch, aber die Quintessenz ist einfach: Es gibt nen krassen dude namens [Doug McKenna](http://www.mathemaesthetics.com/), der hat einfach mal entspannt den kompletten TeX-Kernel neu für sich (closed-source) implementiert. Und den kann man eben in ein E-Book einbetten und dann *zur Laufzeit* Grafiken neu rendern. Im Grund genommen ist genau das der feuchte Traum eines jeden, der hochqualitativen Schriftsatz und Multimedia vereinen will. Keine Ahnung wie universell das funktioniert, aber wer mag, kann sich gerne mal dieses Hilbert-Kurven-Buch ziehen. Ist schon sehr cool.

#### Videos & Grafiken

- manim
- TikZ

## Julia

### Stock-flow consistent models

[Hier](https://github.com/JohannesNaegele/StockFlowConsistentCore.jl) und alter Code.

### Neuronale Netzwerke

Ich hatte mal eine Phase, in der ich in allen möglichen Programmiersprachen (u. a. Julia) einfache deep neural networks implementiert habe. Einfach deswegen, weil ein Klassenkamerad aus irgendeinem Grund mega in NNs reingenerdet war (was ich cool fand) und ich programmieren lernen wollte. Ich werde die files irgendwann mal rauskramen, vielleicht findet die ja jemand nützlich...

## VWL-Projekte

### Helmedag und Arbeitszeitverkürzung (2017)

Im Kern ging es bei dieser Diskussion darum, ob eine umfassende Arbeitszeitverkürzung (AZV) Arbeitsplätze schafft, weil ja nach der Reform sozusagen genauso viel Arbeitszeit insgesamt benötigt wird, wie davor. Dadurch, dass aber weniger pro Kopf gearbeitet wird, werden nun mehr Arbeitnehmer eingestellt. Dieser Position, vor allem vertreten durch Fritz Helmedag und Heinz-Joseph Bontrup, wurde von Heiner Flassbeck entgegengesetzt, dass ja in dem Moment, in welchem die Arbeitnehmer durch die AZV weniger Lohn bekommen, diese weniger Güter nachgefragen werden (das klassischste aller keynesianischen Argumente). Dadurch wird nach dieser Sicht auch weniger Arbeitszeit benötigt um das nachgefragte BIP zu produzieren und die Beschäftigung bleibt in etwa gleich.

Long story short gab es darüber viel Diskussion und Helmedag hat ein [Papier](https://www.tu-chemnitz.de/wirtschaft/vwl2/downloads/paper/helmedag/Nur%20mehr%20Stundenlohn.pdf) geschrieben das die Position Flassbecks vermeintlich in einem Modell widerlegt. Und dieses Papier hat mich unter anderem aus folgenden Gründen massiv getriggert:

1.  Kann man das Modell in ein IS-LM-ähnliches (injection-leakages) Modell überführen. Und dann ist sofort klar, warum man auf das beschäftigungsfördernde Resultat kommt, denn sog. autonome Nachfrage vom Staat (u. a.) besteht unabhängig von den Arbeitnehmern; diese geben einfach immer einen Teil ihres Einkommens wieder aus. Daher muss das BIP (und damit die Gesamtarbeitszeit) konstant bleiben, wenn sich in der Verteilung zwischen Arbeitnehmern und Arbeitgebern nichts ändert (was bei den unterstellten konstanten realen Stückkosten der Fall ist). 
2.  Aus damaliger Sicht wird nicht immer klar zwischen realer und nominaler Produktivität (bzw. Lohnstückkosten) unterschieden. Ob das wirklich ein Problem darstellt, oder ob ich mich da verrannt habe, ich müsste ich nochmal prüfen. Meine Sicht war, dass in dem Modell lediglich das nominale BIP konstant unter der goldenen Lohnregel ist, aber nicht das reale. Dadurch folgt, dass zwar die Beschäftigung mit der nominalen Produktivität fällt, aber eben nicht mit per se mit der realen.
3.  Dauernd war die Rede von dem "saldenmechanischen Modell". Bei näherer Betrachtung stellt sich aber raus, dass stillschweigend BIP = BNE unterstellt wurde. Sowas wie Primäreinkommen gibt es also nicht. Das tut zwar nichts zur eigentlichen Sache, ist aber aus handwerklicher bzw. saldenmechanischer Sicht und aus Konsistenzgründen eine Katastrophe.

Summa summarum kann man halt einfach sagen, dass das Modell halt nicht das tut, was behauptet wird. Das Argument über Nachfrageausfall ist doch in erster Linie  über den Faktor Zeit relevant. Wenn natürlich sofort neue Arbeitnehmer eingestellt werden, dann sinkt auch die Nachfrage nicht. Wenn Neueinstellungen ein halbes Jahr brauchen, dann wahrscheinlich schon. Im Grunde genommen hat man halt also den Wirkungsmechanismus, den man widerlegen möchte, gar nicht im Modell. Ich habe argumentiert, dass man das Modell ja auch insofern erweitern könnte, als dass man die autonome Nachfrage mit den Löhnen wachsen lassen könnte. Man könnte das beispielsweise in einem Mehrperiodenmodell motivieren, in welchem die autonomen Ausgaben von Steuern (und somit von den Löhnen) abhängen, sich aber nur alle paar Perioden anpassen. Wenn man dann gleichzeitig unterstellt, dass Arbeitnehmer nur graduell neu eingestellt werden, dann hätte man genau so ein Szenario. Je nachdem, wie man dann die Parameter wählt landet man dann zwischen den beiden Ausgangspositionen. Aus praktischer Sicht ist dieses Nachfrageausfallargument ähnlich wie ein Multiplikator ja vor allem eine empirische Frage und überhaupt ist gar nicht klar, warum man sich auf diese komplett nachfragegetriebenen Modelle verlassen sollte. Zumal außerdem Erwartungen hier auch wirklich eine große Rolle spielen.

Diese Erkenntnisse habe ich dann versucht in einem ["Paper"](https://mpra.ub.uni-muenchen.de/82109/) formulieren. Mit einem ordentlich peer-reviewten Text hat das natürlich nichts zu tun, insgesamt ist das einfach viel zu viel Gelaber und die meisten Punkte hätte man auch auf zwei Seiten formulieren können. Außerdem merkt man, dass das mein erster geTeXter Text überhaupt war (die Formeln sehen manchmal ziemlich lustig aus) und ich als Schüler keinen Unizugang zu mancher relevanter Literatur hatte. 

Fun fact aus meiner prä-TeX-Phase: Wenn man Excel-Grafiken ordentlich in LaTeX überführen will, kann man folgendes machen: Zunächst installiert man sich Latin Modern und Latin Modern Math in Office und aktiviert Kerning und Ligaturen -- dann sieht die Grafik halbwegs ordentlich aus. Damals (keine Ahnung ob das heute auch so ist) konnte man nicht ordentlich aus Excel nach svg oder pdf exportieren, das war irgendwie verbuggt. Dafür gibt es aber den grandiosen Trick, dass man die Excel-Grafik nach Word exportiert, dort die Papiergröße exakt auf die Maße der Grafik anpasst und dann als pdf druckt :D

Später hab ich meinen Text dann jedenfalls noch als Magazinbeitrag für Laienpublikum auf Makroskop veröffentlich (siehe [Teil 1](https://makroskop.eu/kann-man-arbeit-umverteilen-1/) und [Teil 2](https://makroskop.eu/kann-man-arbeit-umverteilen-2/)). Das fand Helmedag offenbar nicht so witzig und hat eine Replik geschrieben (siehe [hier](https://www.tu-chemnitz.de/wirtschaft/vwl2/downloads/paper/helmedag/Kein_Streit_um_des_Kaisers_Bart_makroskop.pdf)). Meine Antwort finde ich gerade nicht (evtl. wurde die irgendwann offline genommen?), vielleicht finde ich irgendwo noch eine archivierte Datei.

### E-Mails und social media

Am Ende meiner Schullaufbahn habe ich irgendwann angefangen, regelmäßig Professoren anzuschreiben (oder zu -twittern), deren Papiere ich interessant fand. Denn aus meinem privaten Umfeld gab es kaum Menschen, mit denen ich über beispielsweise DSGE diskutieren konnte; das ist dann halt doch einfach alles zu nerdig. Letzten Endes waren da auf jeden Fall ein paar interessante Sachen dabei, die ich hier vielleicht mal hochladen werde.

### Schefold und die Kapitalkontroverse

Kurz zusammengefasst hab ich mal versucht eine Doktorarbeit von Zonghie Han zu replizieren (bzw. Code intelligent zu copy-pasten und bisschen rumzuspielen). Jedenfalls war die Crux, dass wenn man Technologien nicht paarweise vergleicht, sondern über alle Ländern, auf einmal der einzige Fall von Reswitching verschwindet :D files folgen irgendwann noch...

### Econ speed programming und GPU

To be explained; Fernandez-Villaverde

### Hellwig (Landargument und Dezentraler Tausch)

https://blogs.faz.net/fazit/2020/05/03/streit-um-die-schulden-11340/amp/

### Stock-flow consistent modelle (Replication und Paketentwicklung)
