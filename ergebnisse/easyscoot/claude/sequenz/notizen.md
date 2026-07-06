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

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [ ] `v1-direkt.png` nachliefern
- [x] PlantUML rendern -> `v1-plantuml.png` (Weg siehe oben)
- [ ] K4 fuer direktes Bild offen; K2/K3 unabhaengig bestaetigen
- [ ] Matrix + Journal + Commit
