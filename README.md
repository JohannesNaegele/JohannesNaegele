# A guide through my projects and GitHub repositorys

<!--START_SECTION:waka-->
<!--END_SECTION:waka-->

[![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/0-profile-details.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards)
[![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/1-repos-per-language.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards) [![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/2-most-commit-language.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards)
[![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/3-stats.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards) [![](https://raw.githubusercontent.com/JohannesNaegele/JohannesNaegele/main/profile-summary-card-output/github_dark/4-productive-time.svg)](https://github.com/vn7n24fzkq/github-profile-summary-cards)

*This page will hopefully be translated to English some day.*

Hier möchte ich eine kleine (unvollständige) Übersicht zu allem Möglichen, das ich so mache, erstellen. Mittlerweile verliere ich nämlich langsam selbst manchmal den Überblick über alle GitHub-repositorys, sodass das langsam mal an der Zeit ist. Außerdem möchte ich auch gerne Links und Projekte weitergeben, die ich für cool und/oder hilfreich befinde.

Falls jemand etwas interessant findet und/oder mehr Informationen haben möchte, macht gerne ein Issue auf oder schreibt eine Mail.

## Lehre

### Programmierkurs Julia (FSS 2023, 2024)

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

Ausführliche Erklärung [hier](./src/interactive.md).

Siehe https://github.com/JohannesNaegele/pdf.js-precompiled

### Videos & Grafiken

- manim
- TikZ

## Julia

### Stock-flow consistent models

[Hier](https://github.com/JohannesNaegele/Consistent.jl) und [alter Code](https://github.com/JohannesNaegele/StockFlowConsistentCore.jl).

### IfTraits.jl

Dieses Paket implementiert eine bestimmte Syntax für das Design Pattern *Traits* in Julia. Ich bin mir nicht sicher, ob man das in dieser Art überhaupt will und ob diese Umsetzung nicht sowieso ein Problem löst, dass es gar nicht gibt. Naja. Jedenfalls funktioniert's und war auch eine nette Übung, um mal den ganzen Workflow Richtung Julia-registry zu lernen.

### Multi-Armed Bandits (FSS 2023)

Während einer Einführungsveranstaltung zu Reinforcement Learning habe ich (mal wieder) viel zu viel Zeit in irrelevante Programmieraufgaben gesteckt. Zum einen wollte ich besser verstehen, wie man sinnvoll eine große Bibliothek dieser Art aufsetzt. Es ist halt schon ziemlich interessant, dass die diversen Pakete in Python oder Julia zum Teil sehr unterschiedliche Ansätze verfolgen, um Interfaces zu implementieren. In anderen Worten: Es ist nicht trivial, die MDP-Mathe in Code zu gießen. Beispielsweise: Unterscheidung zwischen Environment und Testbed, Multi-Agent-Spiele (braucht es einen Observer zwischen Env und Agent?)

Zum anderen bin ich dann relativ lange an der effizienten Implementierung von Multi-Armed Bandits hängengeblieben. Auch in diesem vermeintlich rudimänteren Setting stößt man nämlich leicht an rechnerische Grenzen (etwa für eine Anzahl an Runden mit 1 Million). Dieser Code ist zum Teil echt nett und könnte in ein sinnvolles Paket gegossen werden; allerdings muss ich dafür nochmal ordentlich Zeit ins Refactoring stecken (auch weil gewisse SIMD-Pakete möglicherweise Kompatibilitätsprobleme haben) und mir über die Integration in die Julia-Paketlandschaft Gedanken machen.

### Neuronale Netzwerke (2018)

Ich hatte mal eine Phase, in der ich in allen möglichen Programmiersprachen (u. a. Julia) einfache deep neural networks implementiert habe. Einfach deswegen, weil ein Klassenkamerad aus irgendeinem Grund mega in NNs reingenerdet war (was ich cool fand) und ich programmieren lernen wollte. Ich werde die files irgendwann mal rauskramen, vielleicht findet die ja jemand nützlich...

## VWL-Projekte

### Helmedag und Arbeitszeitverkürzung (2017)

[Ausführliche Erklärung](./src/azv.md)

### E-Mails und social media

Am Ende meiner Schullaufbahn habe ich irgendwann angefangen, regelmäßig Professoren anzuschreiben (oder zu -twittern), deren Papiere ich interessant fand. Ein paar interessante Auszüge daraus werde ich hier vielleicht mal hochladen.

### Schefold und die Kapitalkontroverse

Replikationsprojekt von [Han/Schefold 2006](https://github.com/JohannesNaegele/Han-Schefold) sowie [Zambelli 2018](https://github.com/JohannesNaegele/Zambelli-Replication).

### Econ speed programming und GPU

To be explained; Fernandez-Villaverde

### Hellwig (Landargument und Dezentraler Tausch)

https://blogs.faz.net/fazit/2020/05/03/streit-um-die-schulden-11340/amp/

[Privates Repo](https://github.com/JohannesNaegele/Hellwig-1976)

### Stock-flow consistent modelle (Replication und Paketentwicklung)

Siehe [hier](https://github.com/JohannesNaegele/Consistent.jl), work in progress.
