# Evaluation: easyscoot / chatgpt / aktivitaet

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| PlantUML-Nachbewertung | 2026-07-13 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easyscoot-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. `v1.puml` liegt vor; Kompilierung und Rendering bleiben offen.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 3 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Fehlerliste: statische Prüfung am 2026-07-13 unauffällig (vollständiger UML-Block, ausgeglichene Klammern und 1 `if`/1 `endif`); Kompilierbarkeit am 2026-07-14 bestaetigt (fehlerfrei gerendert).
- Direktes Bild – UML-Notation korrekt?: Start- und Endknoten, Aktionen, Kontrollflüsse und drei Swimlanes sind erkennbar. Die gestrichelten Verbindungen zum Rechnungssystem sind in diesem Kontrollflussdiagramm nicht eindeutig als UML-Kontroll- oder Objektflüsse notiert. Eine Entscheidung fehlt vollständig; dies wird zusätzlich unter K3 gewertet.

## K2 – Inhaltliche Korrektheit — Score: PlantUML 5/5 · Direktbild 3/5

Abgleich mit `lastenhefte/easyscoot.md`:

- Suche, Auswahl, Weg zum Standort, Buchung/Freischaltung, Nutzung, Nutzungsende und Fahrtzusammenfassung stimmen im Kern mit dem Lastenheft überein.
- Die Preisberechnung ist korrekt dem externen Rechnungssystem zugeordnet.
- Inhaltliche Ablaufabweichung: Die Preisberechnung wird direkt nach „Nutzung beenden“ angestoßen, während die für den Preis benötigten Nutzungsdaten erst danach erfasst werden. Damit ist die Reihenfolge nicht schlüssig.
- „Nutzung beenden (per App)“ liegt in der Swimlane des EasyScoot-Systems, obwohl das Lastenheft diesen Schritt als Kundenhandlung beschreibt.
- PlantUML-Code: Die Kundenhandlung „Nutzung beenden“, anschließende Fahrtdatenerfassung, externe Preisberechnung und Zusammenfassung sind in fachlich schlüssiger Reihenfolge modelliert.

## K3 – Vollständigkeit — Score: PlantUML 5/5 · Direktbild 3/5

- Mindestanforderung erfüllt (Aktivitäten ≥ 5): ja; deutlich mehr als fünf Aktivitäten sind dargestellt.
- Fehlende zentrale Elemente: Die ausdrücklich geforderte Entscheidung, ob ein passender E-Scooter in der Nähe verfügbar ist, fehlt vollständig; folglich fehlen auch beschriftete alternative Ausgänge.
- Alle im Prompt genannten Kernaktivitäten sind vorhanden.
- PlantUML-Code: alle Kernaktivitäten, die geforderte Verfügbarkeitsentscheidung mit Ja-/Nein-Ausgängen, drei Swimlanes sowie Start- und Endknoten sind vorhanden.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: 5, Befunde: gerendert; saubere 3-Swimlane-Struktur (Preis im Rechnungssystem).
- Direktes Bild — Score: 5/5, Befunde: klare drei Swimlanes, gut lesbare Beschriftungen, keine Überlappungen oder abgeschnittenen Elemente. Die gestrichelten Verbindungen bleiben semantisch uneindeutig, beeinträchtigen die optische Lesbarkeit aber kaum.

## PlantUML vs. direkt – Unterschiede

- Inhaltlich vergleichbar, mit gerendertem PlantUML-Layout (2026-07-14): Der Code ergänzt die im Direktbild fehlende Entscheidung und ordnet Nutzungsende, Fahrtdatenerfassung und Preisberechnung fachlich korrekt zu.

## Was hätten wir anders modelliert?

- Nach der Suche eine Entscheidung „Passender E-Scooter verfügbar?“ mit beschrifteten Ausgängen ergänzen.
- Zuerst Nutzungsdaten erfassen, anschließend den Preis durch das Rechnungssystem berechnen lassen und danach die Zusammenfassung erzeugen.
- Das Beenden der Nutzung als Kundenaktivität modellieren.

## Sonstige Beobachtungen

- Das Direktbild wurde am 2026-07-10 gemeinsam mit den beiden anderen Systemen in derselben Chat-Session erzeugt; ein Kontext- bzw. Struktur-Übertrag ist daher möglich.
- Die im Prompt vorgesehenen zwei getrennten Prompt-Schritte wurden nicht mit zwischenzeitlicher Bestätigung ausgeführt.
- Der Dateiname `v1-direkt-chatgpt.png` weicht vom Standardschema `v1-direkt.png` ab; die Originaldatei wurde nicht umbenannt.
