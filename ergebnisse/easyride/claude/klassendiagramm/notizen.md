# Notizen: easyride / claude / klassendiagramm (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~20:35 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Tim
- Prompt: `prompts/klassendiagramm/easyride-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer die Evaluation (K2/K3): `lastenhefte/easyride.md` (offiziell vorhanden)

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session mit Vorkontext
   (zuvor EasyLib/EasyScoot bearbeitet) -> moeglicher Kontext-Einfluss. Fuer den belastbaren
   KI-/System-Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt (Schritt 1 Verstaendnis-Check, dann Schritt 2) nicht als getrennte
   Nachrichten ausgefuehrt; Diagramm direkt erzeugt.
3. Nur PlantUML-Form erzeugt; die geforderte „direkt gezeichnete" Bildform (`v1-direkt.png`)
   fehlt noch -> Zelle DoD-seitig unvollstaendig.

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich (kein lokales plantuml.jar; Download
  blockiert). `v1-plantuml.png/.svg` fehlt; K1 und K4 daher noch nicht final bewertet.

## Wichtige Modellierungsentscheidungen (Begruendung in evaluation.md)
- `Routenhalt` als eigene Klasse (statt Assoziationsklasse) fuer Reihenfolge ({ordered}) und
  die pro Halt aufzunehmenden/abzusetzenden Fahrgaeste (zwei Assoziationen zu `Fahrgast`).
- `Verbindung` als eigene Klasse zwischen genau zwei Haltepunkten, ungerichtet (Notiz), mit
  `durchschnittlicheFahrzeit`.
- „Zentrale" ueber Attribut `istZentrale : boolean` + Constraint-Notiz modelliert (kein
  eigener Subtyp).
- `Fahrgast` dient zugleich als buchender Kunde (eine Klasse); `Fahrer` und `Tablet` getrennt,
  Kernoperationen des Fahrers am `Fahrer`, `Tablet` als Bedienschnittstelle (Notiz).
- `Flotte` als Aggregation der `Fahrzeuge`.
- Kapazitaetsregel (Fahrgaeste <= Sitzplaetze) und Zentrale-Regel als UML-Constraints/Notizen.
- Kernmethoden verteilt: fahrtBuchen (Fahrgast), wartezeitBerechnen/restfahrzeitBerechnen
  (Fahrt), naechstenHaltepunktAbfragen/ankunftBestaetigen (Fahrer).

## Offene Annahmen / Unklarheiten
- Fahrgast = buchender Kunde in einer Klasse zusammengefasst (Lastenheft nutzt beide Begriffe).
- Keine gemeinsame Personen-Oberklasse fuer Fahrer/Fahrgast (Schritt-2-Vorgabe fordert sie
  nicht; bewusst weggelassen).
- `Fahrt`-`Fahrzeug`-Zuteilung als 0..1 modelliert (zum Buchungszeitpunkt evtl. noch offen).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session
- [ ] `v1-direkt.png` (direkt generiertes Bild) nachliefern
- [ ] PlantUML rendern -> `v1-plantuml.png/.svg`; Renderweg notieren
- [ ] K1/K4 in `evaluation.md` finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] Commit: `ergebnis(easyride/claude): klassendiagramm v1 + evaluation`
