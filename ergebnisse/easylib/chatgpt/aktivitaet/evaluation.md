# Evaluation: easylib / chatgpt / aktivitaet

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| PlantUML-Nachbewertung | 2026-07-13 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easylib-v1.md` |
| Rendering-Weg | offen – offizieller PlantUML-Renderer konnte mangels Freigabe nicht geladen werden |

Skalen und Regeln: `evaluation/kriterien.md`. `v1.puml` liegt vor; Kompilierung und Rendering bleiben offen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 3/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; Renderer fehlt.
- Fehlerliste: statische Prüfung am 2026-07-13 unauffällig (vollständiger UML-Block, ausgeglichene Klammern und 2 `if`/2 `endif`); keine Aussage über die Kompilierbarkeit.
- Direktes Bild – UML-Notation korrekt?: Start- und Endknoten, Aktionen, Kontrollflüsse und zwei Entscheidungen mit beschrifteten Kanten sind erkennbar. Die alternativen Zweige werden jeweils ohne expliziten UML-Merge-Knoten zusammengeführt. Das gesamte Diagramm besitzt nur einen Aktivitätsbereich; die im Prompt verlangten drei Swimlanes fehlen, was zusätzlich unter K3 gewertet wird.

## K2 – Inhaltliche Korrektheit — Score: PlantUML 5/5 · Direktbild 4/5

Abgleich mit `lastenhefte/easylib.md`:

- Katalogabfrage, Alternative zwischen Import und manueller Eingabe, Prüfung auf ein bereits vorhandenes Werk, Anlage eines neuen Werks bei Bedarf sowie Anlage und Standortzuweisung eines Exemplars stimmen fachlich mit dem Lastenheft überein.
- Werk und physisches Exemplar werden sauber unterschieden; die eindeutige Exemplar-ID und der Standort aus Etage und Regalnummer sind enthalten.
- Kleinere Ungenauigkeit: „ISBN bzw. Buchdaten erfassen“ steht vor der Katalogabfrage, obwohl die manuelle Erfassung vollständiger Buchdaten laut Lastenheft die Alternative zum Import ist. Für die Katalogsuche wäre zunächst die ISBN bzw. ein Suchkriterium ausreichend.
- PlantUML-Code: Vor der Katalogabfrage werden nur ISBN bzw. Suchdaten erfasst; vollständige manuelle Buchdaten werden erst im Nicht-gefunden-Zweig eingegeben.

## K3 – Vollständigkeit — Score: PlantUML 5/5 · Direktbild 3/5

- Mindestanforderung erfüllt (Aktivitäten ≥ 5): ja; deutlich mehr als fünf Aktivitäten sind dargestellt.
- Beide geforderten Entscheidungen mit beschrifteten Ja-/Nein-Ausgängen und alle verlangten Kernaktivitäten sind vorhanden.
- Fehlende zentrale Elemente: Statt der geforderten Swimlanes Bibliothekar, EasyLib-System und Verbundkatalog existiert nur eine Lane „Bibliothekar“. Dadurch bleibt die Verantwortungszuordnung für Systemprüfung, Katalogabfrage, Import und Speicherung unvollständig.
- PlantUML-Code: alle geforderten Aktivitäten und beide Entscheidungen mit beschrifteten Kanten sind enthalten; die drei verlangten Swimlanes ordnen die Verantwortlichkeiten zu.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: symmetrischer, gut nachvollziehbarer Ablauf, gut lesbare Beschriftungen, keine Überlappungen oder abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Inhaltlich vergleichbar, obwohl das PlantUML-Layout noch nicht gerendert werden konnte: Der Code besitzt im Gegensatz zum Direktbild drei Swimlanes und trennt Suchdaten von der manuellen Vollerfassung.

## Was hätten wir anders modelliert?

- Drei Swimlanes für Bibliothekar, EasyLib-System und Verbundkatalog verwenden und die Aktivitäten den tatsächlich Verantwortlichen zuordnen.
- Die Zweige jeweils mit einem expliziten Merge-Knoten zusammenführen.
- Vor der Katalogabfrage nur ISBN bzw. Suchdaten erfassen und die vollständige manuelle Buchdateneingabe ausschließlich im Nicht-gefunden-Zweig durchführen.

## Sonstige Beobachtungen

- Das Direktbild wurde am 2026-07-10 gemeinsam mit den beiden anderen Systemen in derselben Chat-Session erzeugt; ein Kontext- bzw. Struktur-Übertrag ist daher möglich.
- Die im Prompt vorgesehenen zwei getrennten Prompt-Schritte wurden nicht mit zwischenzeitlicher Bestätigung ausgeführt.
- EasyLib wurde nach einer versehentlichen gemeinsamen Ausgabe mit EasyScoot erneut allein erzeugt; bewertet wird die finale Einzelgrafik.
- Der Dateiname `v1-direkt-chatgpt.png` weicht vom Standardschema `v1-direkt.png` ab; die Originaldatei wurde nicht umbenannt.
