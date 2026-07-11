# Evaluation: easyride / chatgpt / aktivitaet

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easyride-v1.md` |
| Rendering-Weg | nicht anwendbar – nur direkt generiertes PNG vorhanden |

Skalen und Regeln: `evaluation/kriterien.md`. Die Bewertung ist vorläufig, solange PlantUML-Code und PlantUML-Rendering fehlen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 3/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML-Ausgabe und Rendering fehlen.
- Direktes Bild – UML-Notation korrekt?: Start- und Endknoten, Aktionen, Kontrollflüsse, Swimlanes und eine Entscheidung sind erkennbar. Die beiden alternativen Zweige werden jedoch ohne expliziten UML-Merge-Knoten wieder zusammengeführt. Zudem ist die im Prompt zusätzlich verlangte zweite Entscheidung nicht vorhanden; dies wird unter K3 gewertet.

## K2 – Inhaltliche Korrektheit — Score: 5/5 (Direktbild)

Abgleich mit `lastenhefte/easyride.md`:

- Start- und Zielhaltepunkt, Suche nach Route/Fahrzeug, Kapazitätsprüfung, Alternative zwischen Routenerweiterung und neuer Route, Einplanung des Fahrgasts sowie Berechnung und Mitteilung der Wartezeit stimmen mit dem Lastenheft überein.
- Die neue Route beginnt und endet laut Aktivitätsbeschriftung an der Zentrale; die Kapazitätsregel wird vor der Routenerweiterung berücksichtigt.
- Keine erfundenen fachlichen Funktionen im dargestellten Szenario festgestellt.

## K3 – Vollständigkeit — Score: 4/5 (Direktbild)

- Mindestanforderung erfüllt (Aktivitäten ≥ 5): ja; dargestellt sind neun nummerierte Schritte, wobei 5a/5b Alternativen sind.
- Fehlende zentrale Elemente: Der Prompt fordert mindestens zwei Entscheidungen; dargestellt ist nur die Entscheidung „Existierende Route erweiterbar?“. Eine zweite Entscheidung fehlt.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: klare Zweiteilung in Kunde und EasyRide-System, gut lesbare Beschriftungen, keine Überlappungen oder abgeschnittenen Elemente und nachvollziehbarer Fluss.

## PlantUML vs. direkt – Unterschiede

- Noch nicht vergleichbar, da weder PlantUML-Code noch PlantUML-Rendering vorliegen.

## Was hätten wir anders modelliert?

- Eine zweite fachlich sinnvolle Entscheidung ergänzen und alternative Kontrollflüsse mit einem expliziten Merge-Knoten zusammenführen.

## Sonstige Beobachtungen

- Das Direktbild wurde am 2026-07-10 gemeinsam mit den beiden anderen Systemen in derselben Chat-Session erzeugt; ein Kontext- bzw. Struktur-Übertrag ist daher möglich.
- Die im Prompt vorgesehenen zwei getrennten Prompt-Schritte wurden nicht mit zwischenzeitlicher Bestätigung ausgeführt.
- Der Dateiname `v1-direkt-chatgpt.png` weicht vom Standardschema `v1-direkt.png` ab; die Originaldatei wurde nicht umbenannt.
