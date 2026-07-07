# Notizen: easyscoot / claude / aktivitaet (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~21:30 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Lewin
- Prompt: `prompts/aktivitaet/easyscoot-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm),
  Szenario: "E-Scooter ausleihen und nutzen"
- Referenz fuer K2/K3: `lastenhefte/easyscoot.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in derselben laufenden Cowork-Session, in
   der unmittelbar zuvor die Aktivitaetsdiagramme easylib und easyride erzeugt wurden ->
   moeglicher Kontext-Einfluss ueber Systemgrenzen hinweg (gleicher Diagrammtyp, aehnliche
   Struktur/Granularitaet). Fuer den belastbaren Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (v1-direkt.png) fehlt.
4. Review-Schritt: Entwurf wurde Lewin vor dem Ablegen gezeigt und freigegeben; die
   KI-Ausgabe selbst blieb dabei unveraendert.

## Annahmen der KI bei der Generierung
- Kundenkonto besteht bereits; das Szenario beginnt laut Prompt bei der Suche.
- Nein-Zweig ("kein passender E-Scooter") beendet den Vorgang in einem eigenen Endknoten;
  eine Wiederholungsschleife (erneut abfragen) ist nicht modelliert, da nicht gefordert.
- "Leihstatus auf 'in Benutzung' setzen" als systemseitige Wirkung der Buchung, abgeleitet
  aus dem im Lastenheft definierten Leihstatus (in Benutzung oder nicht).
- Rechnungssystem erhaelt die Fahrtdaten von EasyScoot und meldet den Preis zurueck;
  Schnittstellendetails (Datenformat, Zeitpunkt) sind angenommen.
- Die auf dem E-Scooter laufende Software (Mobilfunk-Meldungen: Position, Ladezustand,
  Fahrstatus) ist nicht als eigene Swimlane modelliert; der Prompt fordert genau die
  drei Lanes Kunde / EasyScoot-System / Rechnungssystem.

## Wichtige Modellierungsentscheidungen (Kurzfassung, Details in evaluation.md)
- 3 Swimlanes wie gefordert: Kunde / EasyScoot-System / Rechnungssystem.
- Preisberechnung liegt vollstaendig in der Rechnungssystem-Lane (Kernvorgabe des Prompts).
- Genau eine Entscheidung (Mindestvorgabe: eine) mit beschrifteten Kanten ja/nein; der
  Ja-Zweig enthaelt nur "E-Scooter auswaehlen", der Folgeablauf liegt auf oberster Ebene
  (vermeidet tiefe Verschachtelung und leere Zweige).
- Fahrtdaten (Dauer, Kilometer, Wattstunden) werden von EasyScoot ermittelt, der Preis
  kommt vom Rechnungssystem; die Zusammenfassung zeigt alle vier Werte (Lastenheft).
- 14 Aktionen insgesamt (Mindestanforderung: 5).

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich: Download der plantuml.jar blockiert
  (HTTP 403 vom Proxy; versucht: Maven Central, in dieser Session vor der easylib-Zelle).
  Daher fehlt v1-plantuml.png/.svg; K1/K4 offen. Syntax nur per Sichtpruefung.
- Renderweg des Teams festlegen und hier nachtragen.

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] v1-direkt.png ergaenzt am 2026-07-06 (Cowork-SVG + librsvg-Render; Journal 22:55)
- [ ] PlantUML rendern -> v1-plantuml.png/.svg; Renderweg hier notieren
- [ ] K1/K4 in evaluation.md finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] Commit: ergebnis(easyscoot/claude): aktivitaet v1 + evaluation
