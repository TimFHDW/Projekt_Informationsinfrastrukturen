# Notizen: easylib / claude / aktivitaet (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~21:10 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Lewin
- Prompt: `prompts/aktivitaet/easylib-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm),
  Szenario: "Bibliothekar pflegt ein neues Buchexemplar ein"
- Referenz fuer K2/K3: `lastenhefte/easylib.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session. Vorkontext
   diesmal besonders relevant: Vor der Generierung wurden AGENTS.md, das Lastenheft UND die
   bestehende Zelle easylib/claude/klassendiagramm (inkl. v1.puml) gelesen -> moeglicher
   Kontext-Einfluss ("context bleed"), z. B. Uebernahme der Werk-/Exemplar-Begriffe.
   Fuer den belastbaren Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (v1-direkt.png) fehlt.
4. Review-Schritt: Entwurf wurde Lewin vor dem Ablegen gezeigt und freigegeben; die
   KI-Ausgabe selbst blieb dabei unveraendert.

## Annahmen der KI bei der Generierung
- Reihenfolge gemaess Prompt: erst Katalog-Entscheidung, dann Bestandspruefung. Fachlich
  waere eine Dubletten-/Bestandspruefung per ISBN VOR der Katalogabfrage effizienter.
- Verbundkatalog wird immer zuerst abgefragt; manuelle Eingabe ist Rueckfallebene
  (Lastenheft: Import "statt" manueller Eingabe).
- Standortzuweisung (Etage, Regalnummer) ist fachliche Entscheidung des Bibliothekars;
  die Speicherung uebernimmt das System.
- Szenario auf ein Buch bezogen (ISBN, Verbundkatalog); Hoerbuecher wuerden analog
  eingepflegt, sind aber nicht Teil dieses Szenarios.
- Leihfrist-Mehrdeutigkeit des Lastenhefts betrifft dieses Szenario nicht; kein Einfluss.

## Wichtige Modellierungsentscheidungen (Kurzfassung, Details in evaluation.md)
- 3 Swimlanes wie gefordert: Bibliothekar / EasyLib-System / Verbundkatalog.
- Entscheidung 1 ("gefunden?"): beide Zweige laufen vor der Bestandspruefung wieder zusammen.
- Entscheidung 2 ("Werk bereits im Bestand?") mit expliziten Aktionen in BEIDEN Zweigen
  ("Bestehendes Werk auswaehlen" vs. "Werk (Buch) neu anlegen"), danach gemeinsames
  "Exemplar anlegen" -> Werk- und Exemplar-Ebene klar getrennt.
- 13 Aktionen insgesamt (Mindestanforderung: 5).

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich: Download der plantuml.jar blockiert
  (HTTP 403 vom Proxy; versucht: Maven Central). Daher fehlt v1-plantuml.png/.svg; K1/K4
  offen. Syntax nur per Sichtpruefung (Paarigkeit @startuml/@enduml, if/else/endif).
- Renderweg des Teams festlegen und hier nachtragen.

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [ ] v1-direkt.png (direkt generiertes Bild) nachliefern
- [ ] PlantUML rendern -> v1-plantuml.png/.svg; Renderweg hier notieren
- [ ] K1/K4 in evaluation.md finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] Commit: ergebnis(easylib/claude): aktivitaet v1 + evaluation
