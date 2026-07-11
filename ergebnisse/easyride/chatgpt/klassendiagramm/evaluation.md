# Evaluation: easyride / chatgpt / klassendiagramm

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyride-v1.md` |
| Rendering-Weg | nicht anwendbar – direktes Bild mit integriertem Imagegen-Werkzeug erzeugt |

Skalen und Regeln: `evaluation/kriterien.md`. Die Bewertung ist vorläufig, solange PlantUML-Code und PlantUML-Rendering fehlen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 5/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML-Ausgabe und Rendering fehlen.
- Direktes Bild – UML-Notation korrekt?: Klassenkästen, Komposition, Assoziationen, Multiplizitäten und Notizen sind formal korrekt als UML erkennbar. Die Verbindung zwischen `Verbindung` und `Haltepunkt` ist als einfache Assoziation mit den Multiplizitäten 2 bzw. 0..* dargestellt. Mehrere Linien sind fachlich an falschen Klassen angeschlossen; dies wird ausschließlich unter K2/K3 bewertet.

## K2 – Inhaltliche Korrektheit — Score: 2/5 (Direktbild)

Abgleich mit `lastenhefte/easyride.md`:

- Klassen für Kunde, Fahrer, Fahrzeug, Route, Routenhalt, Haltepunkt, Verbindung, Fahrgast und Buchung sowie die beiden Fachregel-Notizen sind vorhanden.
- Zentrale Fehlzuordnung: `Fahrzeug` ist im Bild mit `Routenhalt` statt mit `Route` verbunden.
- Zentrale Fehlzuordnung: `Routenhalt` ist mit `Verbindung` statt mit `Haltepunkt` verbunden; damit ist der Haltepunkt eines Routenhalts nicht modelliert.
- Die geforderte Beziehung zwischen `Buchung` und `Fahrgast` fehlt.
- Die Verbindung `Buchung`–`Route` ist vorhanden, aber mit „gehört zu“ statt der fachlich präziseren Einplanung bezeichnet.

## K3 – Vollständigkeit — Score: 3/5 (Direktbild)

- Mindestanforderung: für Klassendiagramme nicht anwendbar.
- Vorhanden: alle geforderten Klassen, zentrale Methoden, Multiplizitäten an den gezeichneten Assoziationen, `{ordered}` und beide Fachregel-Notizen.
- Fehlende zentrale Elemente: korrekte Assoziationen Fahrzeug–Route, Routenhalt–Haltepunkt und Buchung–Fahrgast.
- Die Aufnahme- und Absetzbeziehungen zwischen Routenhalt und Fahrgast sind dargestellt.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: scharfes, kontrastreiches Querformat; Klassen und Notizen sind vollständig sichtbar, Beschriftungen überlappen nicht.

## PlantUML vs. direkt – Unterschiede

- Noch nicht vergleichbar, da kein zugehöriger v1-PlantUML-Code und kein PlantUML-Rendering vorliegen.

## Was hätten wir anders modelliert?

- Fahrzeug direkt mit Route, Routenhalt direkt mit Haltepunkt und Buchung direkt mit Fahrgast verbinden; anschließend alle Endmultiplizitäten erneut fachlich prüfen.

## Sonstige Beobachtungen

- Das Bild wurde in einem eigenständigen Imagegen-Durchlauf erzeugt und unverändert als Original abgelegt.
- Der Dateiname `v1-direkt-chatgpt.png` folgt auf Nutzerwunsch dem Schema der ChatGPT-Aktivitätsdiagramme und weicht vom Standardnamen `v1-direkt.png` ab.
