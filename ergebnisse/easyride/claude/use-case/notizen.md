# Notizen: easyride / claude / use-case (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, nachmittags (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Alex
- Prompt: `prompts/use-case/easyride-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer K2/K3: `lastenhefte/easyride.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session, in der zuvor
   die Zelle easylib/claude/use-case (inkl. v1.puml) erstellt wurde -> moeglicher
   Kontext-Einfluss ("context bleed"), z. B. gleiche Skinparam-/Layout-Muster.
   Fuer belastbaren Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check
   ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (v1-direkt.png) fehlt.
4. Auftrag nannte urspruenglich den Ordner aktivitaet/ fuer das Use-Case-Diagramm;
   analog zur easylib-Zelle auf use-case/ korrigiert (aktivitaet/ war bereits belegt).
5. Review-Schritt: Entwurf wurde Alex vor dem Ablegen gezeigt und freigegeben; die
   KI-Ausgabe selbst blieb dabei unveraendert.

## Annahmen der KI bei der Generierung
- Leistungslisten des Lastenhefts als abschliessend behandelt (Prompt-Vorgabe):
  exakt 5 Use Cases, keine zusaetzlichen erfunden.
- Routenplanung (Route anlegen/aendern/erweitern) NICHT als Use Case: systeminterne
  Folge von "Fahrt buchen" ohne eigenen Akteur; gehoert in Aktivitaets-/Sequenzdiagramm.
- Kein include/extend: "Wartezeit abfragen" und "Restfahrzeit abfragen" sind
  eigenstaendige, direkt vom Kunden angestossene Abfragen, keine Teilablaeufe von
  "Fahrt buchen". Im Zweifel weggelassen (Prompt-Vorgabe).
- Die drei unverhandelbaren Fachregeln (ungerichteter Graph mit Fahrzeiten,
  Sitzplatzkapazitaet, Zentrale ohne Ein-/Ausstieg) sind im Use-Case-Diagramm nicht
  darstellbar; sie wirken als Randbedingungen von "Fahrt buchen" und werden in den
  Struktur-/Verhaltensdiagrammen abgebildet.
- Akteur als "Kunde (Fahrgast)" benannt, da das Lastenheft beide Begriffe verwendet
  (Kunde bucht, Fahrgast faehrt mit); Tablet/Smartphone sind Geraete, keine Akteure.
- Umlaute in Bezeichnern als ae/ue-Schreibweise (Rendersicherheit).

## Wichtige Modellierungsentscheidungen (Kurzfassung, Details in evaluation.md)
- Genau 5 Use Cases (Mindestanforderung: 5), Systemgrenze "EasyRide", beide Akteure
  ausserhalb.
- Kunde: 3 Use Cases, Fahrer: 2 Use Cases; keine gemeinsam genutzten Use Cases.
- Keine include/extend-Beziehungen (begruendet, s. o.).
- Klammerzusaetze "(vor/nach Fahrtantritt)" uebernehmen die Praezisierung des
  Lastenhefts direkt in den Use-Case-Namen.

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich: Download der plantuml.jar
  weiterhin blockiert (versucht: GitHub Releases, 2026-07-06). Daher fehlt
  v1-plantuml.png/.svg; K1/K4 offen. Syntax nur per Sichtpruefung
  (@startuml/@enduml, rectangle-Block, Alias-Referenzen).
- Renderweg des Teams festlegen und hier nachtragen.

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [ ] v1-direkt.png (direkt generiertes Bild) nachliefern
- [ ] PlantUML rendern -> v1-plantuml.png/.svg; Renderweg hier notieren
- [ ] K1/K4 in evaluation.md finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] evaluation/ergebnismatrix.md aktualisieren
- [ ] Journal-Eintrag in dokumentation/vorgehen.md
- [ ] Commit: ergebnis(easyride/claude): use-case v1 + evaluation
