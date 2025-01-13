# A guide through my projects and GitHub repositorys

<!--START_SECTION:waka-->
<!--END_SECTION:waka-->

[![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/0-profile-details.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards)
[![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/1-repos-per-language.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards) [![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/2-most-commit-language.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards)
[![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/3-stats.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards) [![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/4-productive-time.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards)

*This page will hopefully be translated to English someday.*

Hier möchte ich eine kleine (sehr unvollständige) Übersicht zu allem Möglichen, das ich so mache, erstellen. Mittlerweile verliere ich nämlich langsam selbst manchmal den Überblick über alle GitHub-repositorys, sodass das langsam mal an der Zeit ist. Außerdem möchte ich auch gerne Links und Projekte weitergeben, die ich für cool und/oder hilfreich befinde.

Falls jemand etwas interessant findet oder mehr Informationen haben möchte, macht gerne ein Issue auf oder schreibt eine Mail.

## Lehre

### Programmierkurs Julia (FSS 2023, 2024)

Über die Jahre habe ich einige Kurse zu R, Julia und Datenanalyse gehalten. Das deutschsprachige Material zum Julia-Einführungskurs findet sich [hier](https://github.com/JohannesNaegele/Programmierkurs-Julia).

### Stochastik I (HWS 2021)

Immerhin hab ich hier wenn schon nicht mega viel inhaltlich, dann doch wenigstens gestalterisch einiges beigesteuert (Videoschnitt, Grafiken, etc.). Die Vorlesung ist cool; jedem der Interesse an einer sauberen maßtheoretischen Einführung in die Stochastik hat, kann ich sie nur empfehlen. Interne Links zum [Legacy-Skript-Repo](https://github.com/JohannesNaegele/Stochastik1) und zum [YouTube-Animationen-Repo](https://github.com/JohannesNaegele/Videos_Stochastik/tree/master/Stochastik).

[YouTube-Playlist](https://youtube.com/playlist?list=PLy5qRKPWp6SBwfc1kn-b66cWc84cOgvqZ) und [Website](https://www.wim.uni-mannheim.de/doering/teaching/hws21/stochastik-1/)

## Abschluss- und sonstige Uniarbeiten

### Bachelorarbeit

Hier ging es darum, die Berechnung genetischer Verwandtschaftsmatrixen mittels GPUs zu beschleunigen. Insbesondere ging es um 1-Bit-Matrixmultiplikation ab der Turing-Generation in Verbindung mit Cutlass. Der Code findet sich [hier](https://github.com/JohannesNaegele/miraculix-BA). Demnächst wird dazu ein verbesserter (nicht-naiver) Tiling-Algorithmus implementiert.

### Masterarbeit

Hier wird es wahrscheinlich um Econophysics gehen, insbesondere wealth-tails.

### Seminar Adaptives MCMC

Ganz nette [Slides](https://github.com/JohannesNaegele/JohannesNaegele/blob/main/src/presentation.pdf).

### Seminar Transformer

Ebenfalls nette Slides, aber ohne Erklärung nicht wirklich hilfreich. Deshalb [intern](https://github.com/JohannesNaegele/Transformer-Seminar/tree/main/presentation).

### Seminar zu Energienetzen

Tatsächlich kam hierbei wenig Gehaltvolles bei rum (und ich habe immer noch nicht verstanden, wie genau powerflow equations funktionieren). Allerdings habe ich mittlerweile eine ganz gute Ahnung, wie Energienetzmodelle mit PyPSA und Datenbanksystem umgesetzt werden; außerdem bin ich der Überzeugung, dass eine Integration von Wetter- und Energienetzmodellen in Konjunkturmodelle gewinnbringend wäre (work in progress).

### Klimavorlesung

[Hier](https://github.com/JohannesNaegele/MaKli.jl) ein paar nette Grafiken zu einer Klimamodellierungsvorlesung, die aber zum Teil etwas Kontext benötigen.

## Programmierung

### Stock-flow consistent models (Replikation und Paketentwicklung in Julia)

Ein sträflich vernachlässigtes Projekt ist die Implementierung einer Julia-Bibliothek für SFC models. Die Idee war: Julia ist grundsätzlich schneller als R (was für viele, aber längst nicht alle Anwendungen egal ist). Außerdem sind Autodiff-Fähigkeiten und die dazugehörige Paketlandschaft relevant. Das ist alles relevant für Parameterkalibrierung, Modelinitialisierung und stochastische Modifikationen (Adjoint Methods, auch etwa bayesianische Kalibrierung). Ich bin mir aber noch nicht ganz im Klaren darüber, ob die Paket-API und -Syntax aktuell gut ist. Das ist btw auch interessant, weil sich natürlich die Dynare-Julia-Implementierungen mit ähnlichen Fragen befassen müssen.

Ich bin mittlerweil ziemlich desillusioniert was die Sinnhaftigkeit dieses Modellierungsansatzes angeht. Dazu ein andermal mehr. TLDR: Aus verschiedenen Gründen hätte ich gerne mehr Stochastik drin, es ist aber methodologisch unklar wie man diese wählt oder kalibriert und daher eigentlich immer ziemlich arbiträt. Das Fass zum Überlaufen gebracht hat damals mein Replikationsprojekt eines österreichischen Modells, das auf den ersten Blick gut aussah – die österreichischen Daten wurde nett approximiert und prognostiziert. Nur leider stellte sich bei der unmittelbaren Übertragung auf deutsche Daten raus, dass für fast alle naheliegenden Parameterkalibrierungen das Modell einfach unmittelbar crasht (Fixpunkt mit Nonsens-BIP etc.).

Aktueller Code [hier](https://github.com/JohannesNaegele/Consistent.jl) und [alter Code](https://github.com/JohannesNaegele/StockFlowConsistentCore.jl).

### IfTraits.jl (2023)

[Dieses](https://github.com/JohannesNaegele/IfTraits.jl) Julia-Paket implementiert eine bestimmte Syntax für das Design Pattern *Traits* in Julia. Ich bin mir nicht sicher, ob man das in dieser Art überhaupt will und ob diese Umsetzung nicht sowieso ein Problem löst, dass es gar nicht gibt. Naja. Jedenfalls funktioniert's und war auch eine nette Übung, um mal den ganzen Workflow Richtung Julia-registry zu lernen.

### Multi-Armed Bandits in Julia (FSS 2023)

Während einer Einführungsveranstaltung zu Reinforcement Learning habe ich (mal wieder) viel zu viel Zeit in irrelevante Programmieraufgaben gesteckt. Zum einen wollte ich besser verstehen, wie man sinnvoll eine große Bibliothek dieser Art aufsetzt. Es ist halt schon ziemlich interessant, dass die diversen Pakete in Python oder Julia zum Teil sehr unterschiedliche Ansätze verfolgen, um Interfaces zu implementieren. In anderen Worten: Es ist nicht trivial, die MDP-Mathe in Code zu gießen. Beispielsweise: Unterscheidung zwischen Environment und Testbed, Multi-Agent-Spiele (braucht es einen Observer zwischen Env und Agent?)

Zum anderen bin ich dann relativ lange an der effizienten Implementierung von Multi-Armed Bandits hängengeblieben. Auch in diesem vermeintlich rudimänteren Setting stößt man nämlich leicht an rechnerische Grenzen (etwa für eine Anzahl an Runden mit 1 Million). Dieser Code ist zum Teil echt nett und könnte in ein sinnvolles Paket gegossen werden; allerdings muss ich dafür nochmal ordentlich Zeit ins Refactoring stecken (auch weil gewisse SIMD-Pakete möglicherweise Kompatibilitätsprobleme haben) und mir über die Integration in die Julia-Paketlandschaft Gedanken machen.

### CameraMagic (2019)

Dies war ein völlig überambitioniertes, aber wie ich finde trotzdem interessantes, Projekt (ich sag nur: Seilzuggeber!). Erklärung kommt noch; Buzzwords sind computer vision und homography estimation.

### Neuronale Netzwerke (2018)

Ich hatte mal eine Phase, in der ich in allen möglichen Programmiersprachen (u. a. Julia) einfache deep neural networks implementiert habe. Einfach deswegen, weil ein Klassenkamerad sich aus irgendeinem Grund mega in NNs reingenerdet hatte (was ich cool fand) und ich programmieren lernen wollte. Ich werde die files irgendwann mal rauskramen, vielleicht findet die ja jemand nützlich...

## VWL-Projekte

### Helmedag und Arbeitszeitverkürzung (2017)

Ein Projekt aus Schulzeiten, hier die [ausführliche Erklärung](./src/azv.md).

### E-Mails und social media

Am Ende meiner Schullaufbahn habe ich irgendwann angefangen, regelmäßig Professoren anzuschreiben (oder zu -twittern), deren Papiere ich interessant fand. Ein paar interessante Auszüge daraus werde ich hier vielleicht mal hochladen.

### Schefold und die Kapitalkontroverse

Replikationsprojekt von [Han/Schefold 2006](https://github.com/JohannesNaegele/Han-Schefold) sowie [Zambelli 2018](https://github.com/JohannesNaegele/Zambelli-Replication) basierend auf meinem Paket [Sraffa.jl](https://github.com/JohannesNaegele/Sraffa.jl).

Eventuell folgt ein Monsterprojekt, nämlich eine Videoreihe mit manim zur Kapitaltheorie. Wird aber gigantisch viel Zeit beanspruchen.

### Econ speed programming, GPU, Particle Filter

Ich bin nach wie vor großer Fan der Arbeiten von Fernandez-Villaverde et al. und hatte da ein paar Spielereien (zum Bespiele [diese](https://github.com/davidzarruk/Parallel_Computing/pull/4) PR). Das meiste davon wird aber niemandem nützen und sollte komplett neu aufgerollt werden (insbesondere [SMC-Filter](https://github.com/JohannesNaegele/Toy-SMC)). [Das hier](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python) war damals ein cooles, instruktives Repo.

### Hellwig (Landargument und Dezentraler Tausch)

https://blogs.faz.net/fazit/2020/05/03/streit-um-die-schulden-11340/amp/

[Privates Repo](https://github.com/JohannesNaegele/Hellwig-1976)

### Mean-field games (Replikation: Tankov)

To be explained; [here](https://github.com/JohannesNaegele/MeanFieldSim.jl) the code.

## Data science

### Degustation

Seit einiger Zeit sammle ich ausgiebig Daten zu (Specialty) Coffee Brews. Ob man daraus was lernen kann, wird sich noch rausstellen :D

## LaTeX und Publishing

### Garamond-Math (2024)

Ich bin ein großer Fan der Schriftart Garamond. Wie sich rausstellt, gibt es dafür keine bzw. nur ziemlich primitive Mathe-Fonts. Deshalb habe ich mich mal daran gesetzt, an einer bestehenden Font weiter zu schrauben. Das ist aber alles noch nicht produktionsreif und wird noch einige Stunden brauchen. Manches ist schon recht hübsch, anderes ist noch ziemlicher Pfusch (vor allem die Glyphen für small size).

### Beamer templates (2020)

Hier ein eher mäßig guter [Versuch](https://github.com/JohannesNaegele/Beamer/blob/master/Template.pdf).

Oder [confidential](https://github.com/JohannesNaegele/Mannheim-template).

### Interaktive Dokumente (2020)

Ausführliche Erklärung [hier](./src/interactive.md).

Intern [hier](https://github.com/JohannesNaegele/pdf.js-precompiled) und [hier](https://github.com/JohannesNaegele/Interactive-PDF).

### Videos & Grafiken

- manim
- TikZ

## Sonstiger Quatsch

Hier ein (mittlerweile veraltetes) [Musik-Ranking](https://github.com/JohannesNaegele/Best-of-Genre).
