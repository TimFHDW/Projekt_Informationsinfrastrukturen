# Evaluation: easyscoot / chatgpt / aktivitaet

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easyscoot-v1.md` |
| Rendering-Weg | nicht anwendbar – nur direkt generiertes PNG vorhanden |

Skalen und Regeln: `evaluation/kriterien.md`. Die Bewertung ist vorläufig, solange PlantUML-Code und PlantUML-Rendering fehlen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 3/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML-Ausgabe und Rendering fehlen.
- Direktes Bild – UML-Notation korrekt?: Start- und Endknoten, Aktionen, Kontrollflüsse und drei Swimlanes sind erkennbar. Die gestrichelten Verbindungen zum Rechnungssystem sind in diesem Kontrollflussdiagramm nicht eindeutig als UML-Kontroll- oder Objektflüsse notiert. Eine Entscheidung fehlt vollständig; dies wird zusätzlich unter K3 gewertet.

## K2 – Inhaltliche Korrektheit — Score: 3/5 (Direktbild)

Abgleich mit `lastenhefte/easyscoot.md`:

- Suche, Auswahl, Weg zum Standort, Buchung/Freischaltung, Nutzung, Nutzungsende und Fahrtzusammenfassung stimmen im Kern mit dem Lastenheft überein.
- Die Preisberechnung ist korrekt dem externen Rechnungssystem zugeordnet.
- Inhaltliche Ablaufabweichung: Die Preisberechnung wird direkt nach „Nutzung beenden“ angestoßen, während die für den Preis benötigten Nutzungsdaten erst danach erfasst werden. Damit ist die Reihenfolge nicht schlüssig.
- „Nutzung beenden (per App)“ liegt in der Swimlane des EasyScoot-Systems, obwohl das Lastenheft diesen Schritt als Kundenhandlung beschreibt.

## K3 – Vollständigkeit — Score: 3/5 (Direktbild)

- Mindestanforderung erfüllt (Aktivitäten ≥ 5): ja; deutlich mehr als fünf Aktivitäten sind dargestellt.
- Fehlende zentrale Elemente: Die ausdrücklich geforderte Entscheidung, ob ein passender E-Scooter in der Nähe verfügbar ist, fehlt vollständig; folglich fehlen auch beschriftete alternative Ausgänge.
- Alle im Prompt genannten Kernaktivitäten sind vorhanden.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: klare drei Swimlanes, gut lesbare Beschriftungen, keine Überlappungen oder abgeschnittenen Elemente. Die gestrichelten Verbindungen bleiben semantisch uneindeutig, beeinträchtigen die optische Lesbarkeit aber kaum.

## PlantUML vs. direkt – Unterschiede

- Noch nicht vergleichbar, da weder PlantUML-Code noch PlantUML-Rendering vorliegen.

## Was hätten wir anders modelliert?

- Nach der Suche eine Entscheidung „Passender E-Scooter verfügbar?“ mit beschrifteten Ausgängen ergänzen.
- Zuerst Nutzungsdaten erfassen, anschließend den Preis durch das Rechnungssystem berechnen lassen und danach die Zusammenfassung erzeugen.
- Das Beenden der Nutzung als Kundenaktivität modellieren.

## Sonstige Beobachtungen

- Das Direktbild wurde am 2026-07-10 gemeinsam mit den beiden anderen Systemen in derselben Chat-Session erzeugt; ein Kontext- bzw. Struktur-Übertrag ist daher möglich.
- Die im Prompt vorgesehenen zwei getrennten Prompt-Schritte wurden nicht mit zwischenzeitlicher Bestätigung ausgeführt.
- Der Dateiname `v1-direkt-chatgpt.png` weicht vom Standardschema `v1-direkt.png` ab; die Originaldatei wurde nicht umbenannt.
