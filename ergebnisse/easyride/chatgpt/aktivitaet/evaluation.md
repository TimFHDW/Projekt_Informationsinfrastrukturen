# Evaluation: easyride / chatgpt / aktivitaet

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| PlantUML-Nachbewertung | 2026-07-13 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easyride-v1.md` |
| Rendering-Weg | offen – offizieller PlantUML-Renderer konnte mangels Freigabe nicht geladen werden |

Skalen und Regeln: `evaluation/kriterien.md`. `v1.puml` liegt vor; Kompilierung und Rendering bleiben offen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 3/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; Renderer fehlt.
- Fehlerliste: statische Prüfung am 2026-07-13 unauffällig (vollständiger UML-Block, ausgeglichene Klammern und 2 `if`/2 `endif`); keine Aussage über die Kompilierbarkeit.
- Direktes Bild – UML-Notation korrekt?: Start- und Endknoten, Aktionen, Kontrollflüsse, Swimlanes und eine Entscheidung sind erkennbar. Die beiden alternativen Zweige werden jedoch ohne expliziten UML-Merge-Knoten wieder zusammengeführt. Zudem ist die im Prompt zusätzlich verlangte zweite Entscheidung nicht vorhanden; dies wird unter K3 gewertet.

## K2 – Inhaltliche Korrektheit — Score: PlantUML 5/5 · Direktbild 5/5

Abgleich mit `lastenhefte/easyride.md`:

- Start- und Zielhaltepunkt, Suche nach Route/Fahrzeug, Kapazitätsprüfung, Alternative zwischen Routenerweiterung und neuer Route, Einplanung des Fahrgasts sowie Berechnung und Mitteilung der Wartezeit stimmen mit dem Lastenheft überein.
- Die neue Route beginnt und endet laut Aktivitätsbeschriftung an der Zentrale; die Kapazitätsregel wird vor der Routenerweiterung berücksichtigt.
- Keine erfundenen fachlichen Funktionen im dargestellten Szenario festgestellt.
- PlantUML-Code: Der Ablauf entspricht ebenfalls dem Lastenheft; zusätzlich wird der Fall „kein passendes Fahrzeug“ explizit behandelt.

## K3 – Vollständigkeit — Score: PlantUML 5/5 · Direktbild 4/5

- Mindestanforderung erfüllt (Aktivitäten ≥ 5): ja; dargestellt sind neun nummerierte Schritte, wobei 5a/5b Alternativen sind.
- Fehlende zentrale Elemente: Der Prompt fordert mindestens zwei Entscheidungen; dargestellt ist nur die Entscheidung „Existierende Route erweiterbar?“. Eine zweite Entscheidung fehlt.
- PlantUML-Code: mehr als fünf Aktivitäten, zwei Entscheidungen mit beschrifteten Kanten, beide Swimlanes sowie Start- und Endknoten vorhanden.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: klare Zweiteilung in Kunde und EasyRide-System, gut lesbare Beschriftungen, keine Überlappungen oder abgeschnittenen Elemente und nachvollziehbarer Fluss.

## PlantUML vs. direkt – Unterschiede

- Inhaltlich vergleichbar, obwohl das PlantUML-Layout noch nicht gerendert werden konnte: Der Code ergänzt gegenüber dem Direktbild eine zweite Entscheidung „Passendes Fahrzeug gefunden?“ und erfüllt damit die Promptvorgabe vollständiger.

## Was hätten wir anders modelliert?

- Eine zweite fachlich sinnvolle Entscheidung ergänzen und alternative Kontrollflüsse mit einem expliziten Merge-Knoten zusammenführen.

## Sonstige Beobachtungen

- Das Direktbild wurde am 2026-07-10 gemeinsam mit den beiden anderen Systemen in derselben Chat-Session erzeugt; ein Kontext- bzw. Struktur-Übertrag ist daher möglich.
- Die im Prompt vorgesehenen zwei getrennten Prompt-Schritte wurden nicht mit zwischenzeitlicher Bestätigung ausgeführt.
- Der Dateiname `v1-direkt-chatgpt.png` weicht vom Standardschema `v1-direkt.png` ab; die Originaldatei wurde nicht umbenannt.
