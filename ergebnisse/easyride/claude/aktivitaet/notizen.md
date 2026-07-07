# Notizen: easyride / claude / aktivitaet (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~21:20 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Lewin
- Prompt: `prompts/aktivitaet/easyride-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm),
  Szenario: "Kunde bucht eine Fahrt"
- Referenz fuer K2/K3: `lastenhefte/easyride.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in derselben laufenden Cowork-Session, in
   der unmittelbar zuvor das Aktivitaetsdiagramm easylib/claude/aktivitaet erzeugt wurde ->
   moeglicher Kontext-Einfluss ueber Systemgrenzen hinweg (gleicher Diagrammtyp, aehnliche
   Struktur/Granularitaet). Fuer den belastbaren Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (v1-direkt.png) fehlt.
4. Review-Schritt: Entwurf wurde Lewin vor dem Ablegen gezeigt und freigegeben; die
   KI-Ausgabe selbst blieb dabei unveraendert.

## Annahmen der KI bei der Generierung
- Zwei getrennte Entscheidungen statt einer: erst "Route gefunden?", dann "erweiterbar?"
  (Kapazitaet/Strecke) - so ist die Kapazitaetspruefung sichtbar VOR der Erweiterung.
- "Route veraendern" (im Lastenheft neben "erweitern" genannt) nicht als eigener Fall
  modelliert; der Prompt fordert nur die Alternative erweitern / neu anlegen.
- Ablehnungsfall (kein Fahrzeug verfuegbar) nicht modelliert; das Lastenheft beschreibt
  keinen solchen Fall, der Prompt fordert ihn nicht.
- Wartezeit = Zeit, bis das Fahrzeug den Starthaltepunkt erreicht (Lastenheft-Definition).
- Buchungsbestaetigung als generischer Abschluss der Interaktion, kein neues Feature.

## Wichtige Modellierungsentscheidungen (Kurzfassung, Details in evaluation.md)
- 2 Swimlanes wie gefordert: Kunde / EasyRide-System.
- "Neue Route anlegen" als duplizierter Aktionsknoten in beiden Nein-Zweigen (PlantUML
  kennt kein goto; Zusammenfuehrung erfolgt am endif).
- Zentrale-Regel (Beginn/Ende an der Zentrale) als Klammerzusatz im Anlege-Schritt.
- Begriff "Routenhalte" konsistent zur Routenhalt-Klasse in easyride/claude/klassendiagramm.
- Im if-Text Gedankenstrich statt Klammern (verschachtelte Klammern in PlantUML-Bedingungen
  fehleranfaellig).
- 11 Aktionen insgesamt (Mindestanforderung: 5).

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
- [ ] Commit: ergebnis(easyride/claude): aktivitaet v1 + evaluation
