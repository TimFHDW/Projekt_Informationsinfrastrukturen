# Evaluation: easyscoot / chatgpt / klassendiagramm

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-11 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyscoot-v1.md` |
| Rendering-Weg | nicht anwendbar – direktes Bild mit integriertem Imagegen-Werkzeug erzeugt |

Skalen und Regeln: `evaluation/kriterien.md`. Die Bewertung ist vorläufig, solange PlantUML-Code und PlantUML-Rendering fehlen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 5/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML-Ausgabe und Rendering fehlen.
- Direktes Bild – UML-Notation korrekt?: Abstrakte Oberklasse, Generalisierungen, Klassen, Schnittstelle, Enumerationen, Abhängigkeit und Assoziationen mit Multiplizitäten sind formal korrekt erkennbar.

## K2 – Inhaltliche Korrektheit — Score: 4/5 (Direktbild)

Abgleich mit `lastenhefte/easyscoot.md`:

- Kunde, E-Scooter, Fahrt, Flottenmanager, Service-Mitarbeiter, gemeinsame Oberklasse Nutzerkonto, drei Status-Enumerationen und externes Rechnungssystem sind enthalten.
- Die geforderten Kunden-, Scooter- und Fahrtdaten sowie zentrale Methoden sind weitgehend vollständig vorhanden.
- Inhaltliche Ungenauigkeit: Die Abhängigkeit zur Preisberechnung geht im Bild vom `EScooter` statt von `Fahrt` bzw. einer Systemkomponente aus. Der E-Scooter selbst soll laut Lastenheft nicht das Rechnungssystem aufrufen.
- Das Rechnungssystem ist korrekt als Schnittstelle statt als normale Domänenklasse markiert.

## K3 – Vollständigkeit — Score: 4/5 (Direktbild)

- Mindestanforderung: für Klassendiagramme nicht anwendbar.
- Alle im Prompt geforderten Klassen, Attribute, Enumerationswerte, Methoden und Assoziationsmultiplizitäten sind erkennbar vorhanden.
- Kleine Lücke: Die externe Preisberechnung ist vorhanden, aber nicht an der fachlich passenden Quelle angeschlossen.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: klare Hierarchie, saubere Abstände und gut lesbare Attribute; keine abgeschnittenen oder überlappenden Elemente.

## PlantUML vs. direkt – Unterschiede

- Noch nicht vergleichbar, da kein zugehöriger v1-PlantUML-Code und kein PlantUML-Rendering vorliegen.

## Was hätten wir anders modelliert?

- Die Abhängigkeit zum Rechnungssystem von `Fahrt` oder einer EasyScoot-Systemklasse ausgehen lassen, nicht vom E-Scooter.

## Sonstige Beobachtungen

- Das Bild wurde in einem eigenständigen Imagegen-Durchlauf erzeugt und unverändert als Original abgelegt.
- Der Dateiname `v1-direkt-chatgpt.png` folgt auf Nutzerwunsch dem Schema der ChatGPT-Aktivitätsdiagramme.
