# Evaluation: easylib / chatgpt / aktivitaet

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easylib-v1.md` |
| Rendering-Weg | nicht anwendbar – nur direkt generiertes PNG vorhanden |

Skalen und Regeln: `evaluation/kriterien.md`. Die Bewertung ist vorläufig, solange PlantUML-Code und PlantUML-Rendering fehlen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 3/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML-Ausgabe und Rendering fehlen.
- Direktes Bild – UML-Notation korrekt?: Start- und Endknoten, Aktionen, Kontrollflüsse und zwei Entscheidungen mit beschrifteten Kanten sind erkennbar. Die alternativen Zweige werden jeweils ohne expliziten UML-Merge-Knoten zusammengeführt. Das gesamte Diagramm besitzt nur einen Aktivitätsbereich; die im Prompt verlangten drei Swimlanes fehlen, was zusätzlich unter K3 gewertet wird.

## K2 – Inhaltliche Korrektheit — Score: 4/5 (Direktbild)

Abgleich mit `lastenhefte/easylib.md`:

- Katalogabfrage, Alternative zwischen Import und manueller Eingabe, Prüfung auf ein bereits vorhandenes Werk, Anlage eines neuen Werks bei Bedarf sowie Anlage und Standortzuweisung eines Exemplars stimmen fachlich mit dem Lastenheft überein.
- Werk und physisches Exemplar werden sauber unterschieden; die eindeutige Exemplar-ID und der Standort aus Etage und Regalnummer sind enthalten.
- Kleinere Ungenauigkeit: „ISBN bzw. Buchdaten erfassen“ steht vor der Katalogabfrage, obwohl die manuelle Erfassung vollständiger Buchdaten laut Lastenheft die Alternative zum Import ist. Für die Katalogsuche wäre zunächst die ISBN bzw. ein Suchkriterium ausreichend.

## K3 – Vollständigkeit — Score: 3/5 (Direktbild)

- Mindestanforderung erfüllt (Aktivitäten ≥ 5): ja; deutlich mehr als fünf Aktivitäten sind dargestellt.
- Beide geforderten Entscheidungen mit beschrifteten Ja-/Nein-Ausgängen und alle verlangten Kernaktivitäten sind vorhanden.
- Fehlende zentrale Elemente: Statt der geforderten Swimlanes Bibliothekar, EasyLib-System und Verbundkatalog existiert nur eine Lane „Bibliothekar“. Dadurch bleibt die Verantwortungszuordnung für Systemprüfung, Katalogabfrage, Import und Speicherung unvollständig.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: symmetrischer, gut nachvollziehbarer Ablauf, gut lesbare Beschriftungen, keine Überlappungen oder abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Noch nicht vergleichbar, da weder PlantUML-Code noch PlantUML-Rendering vorliegen.

## Was hätten wir anders modelliert?

- Drei Swimlanes für Bibliothekar, EasyLib-System und Verbundkatalog verwenden und die Aktivitäten den tatsächlich Verantwortlichen zuordnen.
- Die Zweige jeweils mit einem expliziten Merge-Knoten zusammenführen.
- Vor der Katalogabfrage nur ISBN bzw. Suchdaten erfassen und die vollständige manuelle Buchdateneingabe ausschließlich im Nicht-gefunden-Zweig durchführen.

## Sonstige Beobachtungen

- Das Direktbild wurde am 2026-07-10 gemeinsam mit den beiden anderen Systemen in derselben Chat-Session erzeugt; ein Kontext- bzw. Struktur-Übertrag ist daher möglich.
- Die im Prompt vorgesehenen zwei getrennten Prompt-Schritte wurden nicht mit zwischenzeitlicher Bestätigung ausgeführt.
- EasyLib wurde nach einer versehentlichen gemeinsamen Ausgabe mit EasyScoot erneut allein erzeugt; bewertet wird die finale Einzelgrafik.
- Der Dateiname `v1-direkt-chatgpt.png` weicht vom Standardschema `v1-direkt.png` ab; die Originaldatei wurde nicht umbenannt.
