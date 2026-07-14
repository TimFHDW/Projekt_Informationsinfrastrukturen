# Evaluation: easyscoot / claude / aktivitaet

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easyscoot-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 5 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Struktur-Vorpruefung (ersetzt kein Rendering): @startuml/@enduml paarig, 1x if/else/endif
  paarig, 3 Swimlanes, ein start und zwei stop (Nein-Zweig + regulaeres Ende – in
  UML zulaessig, mehrere Endknoten), alle Aktionen als :...;
- Direktes Bild – UML-Notation korrekt?: v1-direkt.png ergaenzt (2026-07-06). Sichtpruefung: korrekte Aktivitaetsdiagramm-Notation (Start-/Endknoten inkl. zweitem Endknoten im Nein-Zweig, Aktionen, Entscheidung mit beschrifteten Kanten, 3 Swimlanes). Formale Bewertung durch Teammitglied ausstehend.

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

- PlantUML-Rendering — Score: 5, Befunde: gerendert; klare 3-Swimlane-Struktur inkl. Rechnungssystem.
- Direktes Bild — Score: 5 (vorlaeufig), Befunde: v1-direkt.png sauber lesbar – klare Swimlanes (inkl. Rechnungssystem), keine Ueberlappungen; unabhaengige Bestaetigung ausstehend.

## PlantUML vs. direkt – Unterschiede

- Beide Formen liegen vor (Direktbild + gerendertes PlantUML, 2026-07-14); Zeichenqualitaet siehe K4, Inhalt siehe K1/K2.

## Was haetten wir anders modelliert?

- Wiederholungsschleife statt Abbruch: bei "kein passender E-Scooter" zurueck zur Abfrage
  (repeat-Konstrukt) statt eigenem Endknoten.
- Zweite Entscheidung denkbar (z. B. "Freischaltung erfolgreich?") fuer Fehlerbehandlung.
- Objektfluss ("Fahrtdaten", "Preis" als Objektknoten zwischen den Lanes) fuer praezisere
  UML-Semantik der Systemanbindung.
- Signal-/Ereignisnotation fuer die Mobilfunk-Meldungen des E-Scooters, falls man die
  Scooter-S
## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1) - Bewertung offen
- `v2.puml` und `v2-direkt.png` liegen vor (s. notizen.md, Nachtrag v2). Diese Datei
  bewertet weiterhin v1; die v2-Bewertung (K1-K4) steht aus, u. a. weil das
  PlantUML-Rendering von v2.puml noch fehlt (Umgebung blockiert Renderer, lokal rendern).
- Vorlaeufige Sichtpruefung v2: Mindestanforderungen des Prompts erfuellt (>= 5
  Aktivitaeten, geforderte Entscheidungen mit beschrifteten Kanten, Swimlanes,
  Start-/Endknoten).
