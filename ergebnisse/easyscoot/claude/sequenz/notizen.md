# Notizen: easyscoot / claude / sequenz (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Basti
- Prompt: `prompts/sequenz/easyscoot-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer Evaluation (K2/K3): `lastenhefte/easyscoot.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session mit erheblichem
   Vorkontext (Repo-Regeln, Klassendiagramm easyscoot/claude v1, Lastenheft sowie die zuvor
   erzeugten easylib-/easyride-Sequenz-Zellen im Kontext). Moeglicher Kontext-Einfluss ->
   fuer belastbaren Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (`v1-direkt.png`) wurde
   nicht erzeugt -> Zelle DoD-seitig unvollstaendig.
4. Gleiche Sitzung erzeugte easylib-, easyride- und easyscoot-Sequenz -> auch Typ-interner
   Kontext-Bleed zwischen den Systemen moeglich (aehnliche Fassaden-Struktur der Diagramme).

## Selbst-Check gegen Prompt-Anforderungen
- >= 5 Methodenaufrufe: ja (6: nutzungBeenden, sperren, aktualisiereLeihstatus,
  ermittleFahrtdaten, berechnePreis, setzePreis)
- Jeder synchrone Aufruf mit Antwortpfeil: ja (Selbstaufruf aktualisiereLeihstatus ohne
  expliziten Antwortpfeil, uebliche Notation)
- Geforderte Lebenslinien vorhanden: Kunde (Smartphone-App), EasyScoot-System, E-Scooter
  (Mobilfunk-Software), Fahrt, Rechnungssystem
- Namen konsistent zum Klassendiagramm v1: EScooter, Fahrt, Leihstatus,
  Rechnungssystem.berechnePreis(fahrt)

## Modellierungsentscheidungen / Annahmen
- Bewusste Abweichung vom Prompt-Beispiel: Der Prompt schlaegt
  berechnePreis(dauer, kilometer, wattstunden) vor, das Klassendiagramm definiert
  berechnePreis(fahrt : Fahrt) : double. Die Konsistenzregel (Regel 6 des Basis-Prompts:
  gleiche Namen ueber alle Diagramme) hat Vorrang -> Signatur aus dem Klassendiagramm.
- Im Klassendiagramm gedanklich zu ergaenzen (per Prompt zulaessig, als Note ausgewiesen):
  Systemfassade `EasyScoot` mit nutzungBeenden/aktualisiereLeihstatus (nutzungBeenden ist
  dort als Methode des Kunden modelliert), EScooter.sperren(), Fahrt.ermittleFahrtdaten(),
  Fahrt.setzePreis().
- Annahme: Die Fahrtdaten (Dauer, Kilometer, Wattstunden) liegen zum Zeitpunkt des Beendens
  bereits in der Fahrt vor (aggregiert aus den regelmaessigen Mobilfunk-Meldungen);
  ermittleFahrtdaten() berechnet nur noch die Zusammenfassung.
- Leihstatus-Aktualisierung als Selbstaufruf des Systems (Zustand des EScooter-Fachobjekts
  in EasyScoot), getrennt vom sperren()-Aufruf an die externe Mobilfunk-Software.

## Rendering / Tooling
- Gerendert am 2026-07-06 in der Cowork-Sandbox (Linux): plantuml.jar **1.2019.06**
  (mitgeliefert im npm-Paket `node-plantuml`), Aufruf:
  `java -jar plantuml.jar -charset UTF-8 -tpng v1.puml` -> `v1-plantuml.png`.
- `v1.puml` kompilierte **ohne Korrektur** (kein `v1-korrigiert.puml` noetig).
- Achtung: 1.2019.06 ist eine alte PlantUML-Version. Fuer den einheitlichen Team-Renderweg
  ggf. mit aktueller Version nachrendern und Ergebnis vergleichen.

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easyscoot.png`)
- Erzeugt am 2026-07-07 in laufender Cowork-Session (Claude, im Auftrag von Tim), allein aus
  `prompts/sequenz/easyscoot-v1.md` (Schritt-1-Systembeschreibung + Schritt-2-Szenario). Die
  zugehoerige `v1.puml` wurde auf Anweisung von Tim BEWUSST NICHT angesehen.
- Folge (wichtig): Das Bild ist eine UNABHAENGIGE Generierung aus dem Prompt, NICHT aus der
  `v1.puml` abgeleitet (anders als die Klassendiagramm-/Use-Case-Direktbilder vom 07.07.).
  Damit ist `vergleiche/plantuml-vs-direkt.md` fuer diese Zelle auch inhaltlich belastbar,
  nicht nur bei der Zeichenqualitaet (K4).
- Tooling: eigener Sequenzdiagramm-Generator (Python) -> SVG -> PNG via librsvg-2 + cairo
  (ctypes), 1360 px breit (2x), weisser Hintergrund.
- Inhalt: Szenario „Kunde beendet die Nutzung eines E-Scooters", 5 Lebenslinien (Kunde-App,
  EasyScoot-System, E-Scooter, Fahrt, Rechnungssystem), 5 synchrone Aufrufe mit Antwortpfeilen;
  die Preisberechnung liegt in der Rechnungssystem-Lebenslinie.
- Methodik-Abweichungen: (1) keine frische, isolierte Session; (2) Zweischritt-Prompt nicht als
  getrennte Nachrichten; (3) alle drei Sequenzbilder in einer Session.
- Namensabweichung: AGENTS.md/DoD nennt `vN-direkt.png`; auf Wunsch von Tim mit Systemnamen
  (`v1-direkt-easyscoot.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] `v1-direkt-easyscoot.png` ergaenzt am 2026-07-07 (unabhaengig aus Prompt, siehe Nachtrag)
- [x] PlantUML rendern -> `v1-plantuml.png` (Weg siehe oben)
- [ ] K4 fuer direktes Bild offen; K2/K3 unabhaengig bestaetigen
- [ ] Matrix + Journal + Commit
