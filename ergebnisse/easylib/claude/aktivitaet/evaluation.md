# Evaluation: easylib / claude / aktivitaet

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easylib-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 5 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Struktur-Vorpruefung (ersetzt kein Rendering): @startuml/@enduml paarig, 2x if/else/endif
  paarig, 3 Swimlanes, genau ein start und ein stop, alle Aktionen als :...;
- Direktes Bild – UML-Notation korrekt?: v1-direkt.png ergaenzt (2026-07-06). Sichtpruefung: korrekte Aktivitaetsdiagramm-Notation (Start-/Endknoten, Aktionen, zwei Rauten-Entscheidungen mit beschrifteten Kanten, 3 Swimlanes). Formale Bewertung durch Teammitglied ausstehend.

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

- PlantUML-Rendering — Score: 5, Befunde: gerendert; klare 3-Swimlane-Struktur, gut lesbar.
- Direktes Bild — Score: 5 (vorlaeufig), Befunde: v1-direkt.png sauber lesbar – klare Swimlanes, keine Ueberlappungen, beide Entscheidungen mit beschrifteten Kanten; unabhaengige Bestaetigung ausstehend.

## PlantUML vs. direkt – Unterschiede

- Beide Formen liegen vor (Direktbild + gerendertes PlantUML, 2026-07-14); Zeichenqualitaet siehe K4, Inhalt siehe K1/K2.

## Was haetten wir anders modelliert?

- Bestands-/Dublettenpruefung per ISBN VOR der Verbundkatalog-Abfrage (spart die Abfrage,
  wenn das Werk schon bekannt ist); der Prompt gibt die andere Reihenfolge vor.
- Fehler-/Abbruchpfade ergaenzen (Katalog nicht erreichbar, Bibliothekar bricht ab).
- Objektfluss ("Buchdaten" als Objektknoten zwischen Katalog und Syst
## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1) - Bewertung offen
- `v2.puml` und `v2-direkt.png` liegen vor (s. notizen.md, Nachtrag v2). Diese Datei
  bewertet weiterhin v1; die v2-Bewertung (K1-K4) steht aus, u. a. weil das
  PlantUML-Rendering von v2.puml noch fehlt (Umgebung blockiert Renderer, lokal rendern).
- Vorlaeufige Sichtpruefung v2: Mindestanforderungen des Prompts erfuellt (>= 5
  Aktivitaeten, geforderte Entscheidungen mit beschrifteten Kanten, Swimlanes,
  Start-/Endknoten).

