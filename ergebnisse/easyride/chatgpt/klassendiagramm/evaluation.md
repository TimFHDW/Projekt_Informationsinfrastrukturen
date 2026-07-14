# Evaluation: easyride / chatgpt / klassendiagramm

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| PlantUML-Nachbewertung | 2026-07-13 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyride-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. `v1.puml` liegt vor; Kompilierung und Rendering bleiben offen.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 5 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Fehlerliste: statische Prüfung am 2026-07-13 unauffällig (vollständiger UML-Block und ausgeglichene Blockklammern); Kompilierbarkeit am 2026-07-14 bestaetigt (fehlerfrei gerendert).
- Direktes Bild – UML-Notation korrekt?: Klassenkästen, Komposition, Assoziationen, Multiplizitäten und Notizen sind formal korrekt als UML erkennbar. Die Verbindung zwischen `Verbindung` und `Haltepunkt` ist als einfache Assoziation mit den Multiplizitäten 2 bzw. 0..* dargestellt. Mehrere Linien sind fachlich an falschen Klassen angeschlossen; dies wird ausschließlich unter K2/K3 bewertet.

## K2 – Inhaltliche Korrektheit — Score: PlantUML 5/5 · Direktbild 2/5

Abgleich mit `lastenhefte/easyride.md`:

- Klassen für Kunde, Fahrer, Fahrzeug, Route, Routenhalt, Haltepunkt, Verbindung, Fahrgast und Buchung sowie die beiden Fachregel-Notizen sind vorhanden.
- Zentrale Fehlzuordnung: `Fahrzeug` ist im Bild mit `Routenhalt` statt mit `Route` verbunden.
- Zentrale Fehlzuordnung: `Routenhalt` ist mit `Verbindung` statt mit `Haltepunkt` verbunden; damit ist der Haltepunkt eines Routenhalts nicht modelliert.
- Die geforderte Beziehung zwischen `Buchung` und `Fahrgast` fehlt.
- Die Verbindung `Buchung`–`Route` ist vorhanden, aber mit „gehört zu“ statt der fachlich präziseren Einplanung bezeichnet.
- PlantUML-Code: verwendet `Fahrt` als Buchungs-/Fahrgastkontext und verbindet Fahrzeug–Route, Routenhalt–Haltepunkt sowie Routenhalt–Kunde fachlich korrekt; beide Fachregeln sind notiert.

## K3 – Vollständigkeit — Score: PlantUML 5/5 · Direktbild 3/5

- Mindestanforderung: für Klassendiagramme nicht anwendbar.
- Vorhanden: alle geforderten Klassen, zentrale Methoden, Multiplizitäten an den gezeichneten Assoziationen, `{ordered}` und beide Fachregel-Notizen.
- Fehlende zentrale Elemente: korrekte Assoziationen Fahrzeug–Route, Routenhalt–Haltepunkt und Buchung–Fahrgast.
- Die Aufnahme- und Absetzbeziehungen zwischen Routenhalt und Fahrgast sind dargestellt.
- PlantUML-Code: alle geforderten Konzepte, zentralen Methoden, Assoziationsmultiplizitäten, `{ordered}` sowie beide Constraints sind vorhanden.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: 4, Befunde: gerendert; lesbar, einige laengere Kanten (eingeplant in, liegt an), keine Ueberlappungen.
- Direktes Bild — Score: 5/5, Befunde: scharfes, kontrastreiches Querformat; Klassen und Notizen sind vollständig sichtbar, Beschriftungen überlappen nicht.

## PlantUML vs. direkt – Unterschiede

- Inhaltlich vergleichbar, mit gerendertem PlantUML-Layout (2026-07-14): Der Code korrigiert die fachlich falschen Anschlüsse des Direktbilds und modelliert die geordnete Route vollständig.

## Was hätten wir anders modelliert?

- Fahrzeug direkt mit Route, Routenhalt direkt mit Haltepunkt und Buchung direkt mit Fahrgast verbinden; anschließend alle Endmultiplizitäten erneut fachlich prüfen.

## Sonstige Beobachtungen

- Das Bild wurde in einem eigenständigen Imagegen-Durchlauf erzeugt und unverändert als Original abgelegt.
- Der Dateiname `v1-direkt-chatgpt.png` folgt auf Nutzerwunsch dem Schema der ChatGPT-Aktivitätsdiagramme und weicht vom Standardnamen `v1-direkt.png` ab.
