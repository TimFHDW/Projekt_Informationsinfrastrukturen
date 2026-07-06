# Evaluationskriterien (K1–K4)

Maßstab für jede `evaluation.md`. Immer gegen das **Lastenheft** prüfen, nie gegen eigenes
Wissen. Jedes Kriterium wird mit 1–5 bewertet **und** mit konkreten Befunden belegt
(Fehlerliste, fehlende Elemente). Score ohne Befunde ist ungültig.

## K1 – Syntaktische Korrektheit

PlantUML-Code: Kompiliert er? Wie viele/welche Fehler? Direkt generiertes Bild: Ist die
UML-Notation korrekt (richtige Pfeile, Symbole, Rahmen)?

| Score | Bedeutung |
|---|---|
| 5 | fehlerfrei, kompiliert/notiert ohne Beanstandung |
| 4 | 1–2 triviale Fehler (z. B. Tippfehler in Keyword), in < 1 min behoben |
| 3 | mehrere Fehler, aber lokal korrigierbar |
| 2 | strukturelle Fehler, größerer Umbau zum Rendern nötig |
| 1 | unbrauchbar, kompiliert auch nach Korrekturversuchen nicht / keine gültige UML-Notation |

## K2 – Inhaltliche Korrektheit

Stimmen Klassen, Beziehungen, Akteure, Abläufe, Aufrufe mit dem Lastenheft überein?
Jeden inhaltlichen Fehler konkret auflisten (z. B. „Beziehung X–Y ist im Lastenheft nicht
gedeckt", „Akteur Z erfunden").

| Score | Bedeutung |
|---|---|
| 5 | keine inhaltlichen Fehler gefunden |
| 4 | 1–2 kleinere Ungenauigkeiten |
| 3 | mehrere Fehler, Kern des Systems aber richtig getroffen |
| 2 | viele Fehler oder zentrale Konzepte falsch |
| 1 | widerspricht dem Lastenheft grundlegend / erfundenes System |

## K3 – Vollständigkeit

Fehlen zentrale Elemente aus dem Lastenheft? Zusätzlich harte Mindestanforderungen:
Use-Case-Diagramm ≥ 5 Use Cases · Aktivitätsdiagramm ≥ 5 Aktivitäten ·
Sequenzdiagramm ≥ 5 Methodenaufrufe. **Mindestanforderung verfehlt ⇒ maximal Score 2.**

| Score | Bedeutung |
|---|---|
| 5 | alle zentralen Elemente des Lastenhefts abgebildet |
| 4 | 1–2 periphere Elemente fehlen |
| 3 | einzelne zentrale Elemente fehlen |
| 2 | deutliche Lücken oder Mindestanforderung verfehlt |
| 1 | nur Fragment |

## K4 – Lesbarkeit / Zeichenqualität

Layout, Überlappungen, Beschriftungen, Übersichtlichkeit. **Getrennt bewerten** für das
gerenderte PlantUML-Diagramm und das direkt generierte Bild – diese Differenz speist
`vergleiche/plantuml-vs-direkt.md` und `vergleiche/diagrammtyp-vergleich.md`.

| Score | Bedeutung |
|---|---|
| 5 | sofort lesbar, sauberes Layout |
| 4 | kleinere Layout-Schwächen |
| 3 | lesbar, aber unübersichtlich (Kreuzungen, Gedränge) |
| 2 | schwer lesbar, Elemente überlappen/abgeschnitten |
| 1 | nicht lesbar |

## Ergänzende Pflichtfragen je Evaluation (ohne Score)

- Unterschiede zwischen PlantUML-Rendering und direktem Bild derselben KI?
- Was hätten wir anders modelliert? (fachliche Einschätzung)
- Auffälligkeiten im Generierungsverlauf (aus `notizen.md`)
