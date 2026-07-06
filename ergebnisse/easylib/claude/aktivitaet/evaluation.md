# Evaluation: easylib / claude / aktivitaet

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easylib-v1.md` |
| Rendering-Weg | ausstehend – in dieser Session kein PlantUML-Rendering moeglich |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: offen (Rendering ausstehend)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft – kein Renderlauf moeglich
  (plantuml.jar-Download blockiert, HTTP 403). Im Team-Renderweg pruefen, Ergebnis eintragen.
- Struktur-Vorpruefung (ersetzt kein Rendering): @startuml/@enduml paarig, 2x if/else/endif
  paarig, 3 Swimlanes, genau ein start und ein stop, alle Aktionen als :...;
- Direktes Bild – UML-Notation korrekt?: n. v. – keine "direkt"-Bildform erzeugt (nur PlantUML).

## K2 – Inhaltliche Korrektheit — Score: 5 (vorlaeufig)

Abgleich mit `lastenhefte/easylib.md`, konkrete Befunde:

- Kernanforderung getroffen: Einpflegen von Buchexemplaren mit Wahl zwischen Import aus dem
  zentralen Verbundkatalog und manueller Eingabe ("statt die Daten manuell einzugeben"). ✓
- Standort korrekt als Etage + Regalnummer. ✓
- Werk-/Exemplar-Trennung konsistent zum Klassendiagramm derselben KI: "Werk (Buch) neu
  anlegen" vs. "Exemplar anlegen" als getrennte Aktionen. ✓
- Rollenverteilung plausibel: fachliche Schritte beim Bibliothekar, Datenoperationen im
  EasyLib-System, Verbundkatalog als externes System in eigener Swimlane. ✓
- Keine erfundenen Features. ✓
- Anmerkungen (keine Fehler): "Suchanfrage bearbeiten"/"Suchergebnis zurueckliefern" und
  "Bestaetigung anzeigen" sind naheliegende Detaillierungen ohne Lastenheft-Wortlaut; die
  Bestandspruefung ("Werk bereits im Bestand?") ist durch den Prompt vorgegeben, nicht
  durchs Lastenheft.

## K3 – Vollstaendigkeit — Score: 5 (vorlaeufig)

- Mindestanforderung erfuellt (Aktivitaeten >= 5): ja – 13 Aktionen.
- Alle 7 im Prompt geforderten Pflicht-Aktivitaeten enthalten; beide geforderten
  Entscheidungen mit beschrifteten Kanten (ja/nein); 3 Swimlanes; Start- und Endknoten.
- Fehlende zentrale Elemente: keine fuer das geforderte Szenario. Peripher, vom Szenario
  nicht verlangt: Fehler-/Abbruchpfade (Verbundkatalog nicht erreichbar, Vorgang abbrechen),
  Hoerbuch-Variante.

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: offen, Befunde: noch nicht gerendert.
- Direktes Bild — Score: n. v., Befunde: keine "direkt"-Bildform erzeugt.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden, kein direktes Bild, kein Rendering.

## Was haetten wir anders modelliert?

- Bestands-/Dublettenpruefung per ISBN VOR der Verbundkatalog-Abfrage (spart die Abfrage,
  wenn das Werk schon bekannt ist); der Prompt gibt die andere Reihenfolge vor.
- Fehler-/Abbruchpfade ergaenzen (Katalog nicht erreichbar, Bibliothekar bricht ab).
- Objektfluss ("Buchdaten" als Objektknoten zwischen Katalog und System) fuer praezisere
  UML-Semantik.
- Verallgemeinerung auf "Medium einpflegen" (Buch + Hoerbuch) statt nur Buch.

## Sonstige Beobachtungen

- Methodik-Abweichungen (laufende Session mit Vorkontext inkl. Klassendiagramm derselben
  KI; nur PlantUML-Form; kein Rendering) – Details in `notizen.md`.
