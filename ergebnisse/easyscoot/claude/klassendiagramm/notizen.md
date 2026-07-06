# Notizen: easyscoot / claude / klassendiagramm (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~20:40 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Tim
- Prompt: `prompts/klassendiagramm/easyscoot-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer die Evaluation (K2/K3): `lastenhefte/easyscoot.md` (offiziell vorhanden)

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session mit Vorkontext
   (zuvor EasyLib/EasyRide bearbeitet) -> moeglicher Kontext-Einfluss. Fuer den belastbaren
   KI-/System-Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt (Verstaendnis-Check, dann Diagramm) nicht als getrennte Nachrichten
   ausgefuehrt; Diagramm direkt erzeugt.
3. Nur PlantUML-Form erzeugt; „direkt gezeichnete" Bildform (`v1-direkt.png`) fehlt noch
   -> Zelle DoD-seitig unvollstaendig.

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich (kein lokales plantuml.jar; Download
  blockiert). `v1-plantuml.png/.svg` fehlt; K1 und K4 daher noch nicht final bewertet.

## Wichtige Modellierungsentscheidungen (Begruendung in evaluation.md)
- Gemeinsame abstrakte Oberklasse `Nutzer` fuer `Kunde`, `Flottenmanager` und
  `Service-Mitarbeiter` (alle mit Nutzerkonto) – wie im Prompt zur Pruefung gestellt.
- `Fahrstatus`, `Leihstatus`, `Wartungsstatus` als Enumerationen mit den Lastenheft-Werten.
- `Rechnungssystem` als «external system» mit Abhaengigkeit von `Fahrt` (nur angebunden,
  berechnet den Preis).
- `Fahrt` traegt Dauer, gefahrene Kilometer, verbrauchte Wattstunden und Preis und verbindet
  `Kunde` und `EScooter`.
- `Flotte` als Aggregation der `EScooter`; `Ladestation` und `Position` als eigene Klassen.
- `geschaetzteRestfahrzeit` als abgeleitetes Attribut (`/`) am `EScooter` markiert.

## Offene Annahmen / Unklarheiten
- `Nutzer`-Oberklasse mit minimalem gemeinsamem Attribut (`nutzername`); rollenspezifische
  Daten liegen in den Unterklassen (nur `Kunde` ist im Lastenheft datenreich beschrieben).
- `Position` als eigene Wertklasse (Breite/Laenge); im Lastenheft nur „Position" genannt.
- `ladestand` als Prozentwert (int) interpretiert (Filter „<= 50 %").
- Buchen/Freischalten/Beenden am `Kunde`, Wartungsmodus am `Service-Mitarbeiter` platziert.

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session
- [ ] `v1-direkt.png` (direkt generiertes Bild) nachliefern
- [ ] PlantUML rendern -> `v1-plantuml.png/.svg`; Renderweg notieren
- [ ] K1/K4 in `evaluation.md` finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] Commit: `ergebnis(easyscoot/claude): klassendiagramm v1 + evaluation`
