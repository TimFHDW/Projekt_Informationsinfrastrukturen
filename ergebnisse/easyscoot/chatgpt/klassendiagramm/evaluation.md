# Evaluation: easyscoot / chatgpt / klassendiagramm

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| PlantUML-Nachbewertung | 2026-07-13 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyscoot-v1.md` |
| Rendering-Weg | offen – offizieller PlantUML-Renderer konnte mangels Freigabe nicht geladen werden |

Skalen und Regeln: `evaluation/kriterien.md`. `v1.puml` liegt vor; Kompilierung und Rendering bleiben offen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 5/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; Renderer fehlt.
- Fehlerliste: statische Prüfung am 2026-07-13 unauffällig (vollständiger UML-Block und ausgeglichene Blockklammern); keine Aussage über die Kompilierbarkeit.
- Direktes Bild – UML-Notation korrekt?: Abstrakte Oberklasse, Generalisierungen, Klassen, Schnittstelle, Enumerationen, Abhängigkeit und Assoziationen mit Multiplizitäten sind formal korrekt erkennbar.

## K2 – Inhaltliche Korrektheit — Score: PlantUML 5/5 · Direktbild 4/5

Abgleich mit `lastenhefte/easyscoot.md`:

- Kunde, E-Scooter, Fahrt, Flottenmanager, Service-Mitarbeiter, gemeinsame Oberklasse Nutzerkonto, drei Status-Enumerationen und externes Rechnungssystem sind enthalten.
- Die geforderten Kunden-, Scooter- und Fahrtdaten sowie zentrale Methoden sind weitgehend vollständig vorhanden.
- Inhaltliche Ungenauigkeit: Die Abhängigkeit zur Preisberechnung geht im Bild vom `EScooter` statt von `Fahrt` bzw. einer Systemkomponente aus. Der E-Scooter selbst soll laut Lastenheft nicht das Rechnungssystem aufrufen.
- Das Rechnungssystem ist korrekt als Schnittstelle statt als normale Domänenklasse markiert.
- PlantUML-Code: Die Preisabhängigkeit geht korrekt von `Fahrt` zum externen Rechnungssystem; die Statuswerte und Wartungsfunktionen entsprechen dem Lastenheft.

## K3 – Vollständigkeit — Score: PlantUML 5/5 · Direktbild 4/5

- Mindestanforderung: für Klassendiagramme nicht anwendbar.
- Alle im Prompt geforderten Klassen, Attribute, Enumerationswerte, Methoden und Assoziationsmultiplizitäten sind erkennbar vorhanden.
- Kleine Lücke: Die externe Preisberechnung ist vorhanden, aber nicht an der fachlich passenden Quelle angeschlossen.
- PlantUML-Code: alle geforderten Klassen, Attribute, Status-Enumerationen, Methoden, Generalisierungen, Multiplizitäten und die externe Schnittstelle sind vorhanden.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: klare Hierarchie, saubere Abstände und gut lesbare Attribute; keine abgeschnittenen oder überlappenden Elemente.

## PlantUML vs. direkt – Unterschiede

- Inhaltlich vergleichbar, obwohl das PlantUML-Layout noch nicht gerendert werden konnte: Der Code bindet das Rechnungssystem fachlich korrekt an `Fahrt` statt an den E-Scooter an.

## Was hätten wir anders modelliert?

- Die Abhängigkeit zum Rechnungssystem von `Fahrt` oder einer EasyScoot-Systemklasse ausgehen lassen, nicht vom E-Scooter.

## Sonstige Beobachtungen

- Das Bild wurde in einem eigenständigen Imagegen-Durchlauf erzeugt und unverändert als Original abgelegt.
- Der Dateiname `v1-direkt-chatgpt.png` folgt auf Nutzerwunsch dem Schema der ChatGPT-Aktivitätsdiagramme.
