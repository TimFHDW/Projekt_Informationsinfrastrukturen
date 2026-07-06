# Evaluation: easyscoot / claude / aktivitaet

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easyscoot-v1.md` |
| Rendering-Weg | ausstehend – in dieser Session kein PlantUML-Rendering moeglich |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: offen (Rendering ausstehend)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft – kein Renderlauf moeglich
  (plantuml.jar-Download blockiert, HTTP 403). Im Team-Renderweg pruefen, Ergebnis eintragen.
- Struktur-Vorpruefung (ersetzt kein Rendering): @startuml/@enduml paarig, 1x if/else/endif
  paarig, 3 Swimlanes, ein start und zwei stop (Nein-Zweig + regulaeres Ende – in
  UML zulaessig, mehrere Endknoten), alle Aktionen als :...;
- Direktes Bild – UML-Notation korrekt?: n. v. – keine "direkt"-Bildform erzeugt (nur PlantUML).

## K2 – Inhaltliche Korrektheit — Score: 5 (vorlaeufig)

Abgleich mit `lastenhefte/easyscoot.md`, konkrete Befunde:

- Ablauf deckungsgleich mit dem Lastenheft: abfragen -> Liste freier E-Scooter (Standort,
  Ladestand, restliche Fahrzeit) -> zum Standort begeben -> dort buchen und freischalten ->
  nutzen -> Beenden per Smartphone -> Zusammenfassung. ✓
- Zusammenfassung mit exakt den vier Lastenheft-Werten (Dauer, gefahrene Kilometer,
  verbrauchte Wattstunden, Preis). ✓
- Kernvorgabe erfuellt: Preisberechnung NICHT in EasyScoot, sondern in der Swimlane des
  angebundenen Rechnungssystems. ✓
- Leihstatus "in Benutzung" beim Freischalten gesetzt – Begriff aus dem Lastenheft
  (Flottenmanager-Sicht), hier als Wirkung der Buchung. ✓
- Keine erfundenen Features (keine Bezahlfunktion in der App, kein Bewertungssystem,
  keine Kontoanlage im Szenario). ✓
- Anmerkungen (keine Fehler): "Buchung registrieren", "Fahrtdaten ermitteln/uebermitteln"
  und "Preis an EasyScoot uebermitteln" sind naheliegende Detaillierungen der Anbindung
  ohne woertliche Lastenheft-Entsprechung.

## K3 – Vollstaendigkeit — Score: 5 (vorlaeufig)

- Mindestanforderung erfuellt (Aktivitaeten >= 5): ja – 14 Aktionen.
- Alle 7 im Prompt geforderten Pflicht-Aktivitaeten enthalten (verfuegbare E-Scooter
  abfragen, auswaehlen, zum Standort begeben, buchen und freischalten, nutzen, Nutzung
  beenden, Zusammenfassung anzeigen); 1 Entscheidung (Mindestvorgabe) mit beschrifteten
  Kanten; 3 Swimlanes; Start- und Endknoten.
- Fehlende zentrale Elemente: keine fuer das geforderte Szenario. Peripher, vom Szenario
  nicht verlangt: Wiederholungsschleife bei erfolgloser Suche, Fehlerpfade (Freischalten
  schlaegt fehl), Flottenmanager-/Service-Ablaeufe (andere Szenarien).

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: offen, Befunde: noch nicht gerendert.
- Direktes Bild — Score: n. v., Befunde: keine "direkt"-Bildform erzeugt.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden, kein direktes Bild, kein Rendering.

## Was haetten wir anders modelliert?

- Wiederholungsschleife statt Abbruch: bei "kein passender E-Scooter" zurueck zur Abfrage
  (repeat-Konstrukt) statt eigenem Endknoten.
- Zweite Entscheidung denkbar (z. B. "Freischaltung erfolgreich?") fuer Fehlerbehandlung.
- Objektfluss ("Fahrtdaten", "Preis" als Objektknoten zwischen den Lanes) fuer praezisere
  UML-Semantik der Systemanbindung.
- Signal-/Ereignisnotation fuer die Mobilfunk-Meldungen des E-Scooters, falls man die
  Scooter-Software doch als eigenen Bereich abbilden wollte.

## Sonstige Beobachtungen

- Methodik-Abweichungen (gleiche Session wie easylib- und easyride-Aktivitaetsdiagramm
  unmittelbar zuvor -> moeglicher Struktur-Uebertrag zwischen Systemen; nur PlantUML-Form;
  kein Rendering) – Details in `notizen.md`.
