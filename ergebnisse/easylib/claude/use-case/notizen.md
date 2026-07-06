# Notizen: easylib / claude / use-case (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, nachmittags (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Alex
- Prompt: `prompts/use-case/easylib-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer K2/K3: `lastenhefte/easylib.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session. Vor der
   Generierung wurden AGENTS.md, das Lastenheft und die bestehende Zelle
   easylib/claude/aktivitaet (inkl. v1.puml, notizen.md) gelesen -> moeglicher
   Kontext-Einfluss ("context bleed"). Fuer belastbaren Vergleich in frischer
   Session reproduzieren.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check
   ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (v1-direkt.png) fehlt.
4. Auftrag nannte urspruenglich den Ordner aktivitaet/ fuer das Use-Case-Diagramm;
   nach Rueckfrage auf use-case/ korrigiert.
5. Review-Schritt: Entwurf wurde Alex vor dem Ablegen gezeigt und freigegeben; die
   KI-Ausgabe selbst blieb dabei unveraendert.

## Annahmen der KI bei der Generierung
- Import aus Verbundkatalog als <<extend>> (nicht <<include>>): laut Lastenheft optional
  ("wahlweise ... statt manuell"), das Einpflegen ist ohne Import vollstaendig.
- "Bestand durchsuchen" und "Standort/Status einsehen" je EIN Use Case, gemeinsam von
  Bibliothekar und Kunde genutzt (Prompt-Vorgabe fuer Ersteres; analog angewandt).
- Leihfrist-Mehrdeutigkeit: Annahme "Verlaengerung nur, wenn KEINE andere Reservierung
  vorliegt" (fachlich plausibel, Original vermutlich Formulierungsfehler). Auf
  Use-Case-Ebene nur Vorbedingung von "Leihfrist verlaengern", kein Diagrammeffekt.
- Kein eigener Use Case "Mahnbescheid ausstellen": Lastenheft fordert nur die Uebersicht
  ueberfaelliger Ausleihen; das Ausstellen passiert ausserhalb des Systems.
- Einschraenkungen (Konto loeschen nur ohne offene Ausleihen; kein Einblick in fremde
  Kundendaten) als Vor-/Randbedingungen aufgefasst, nicht als eigene Use Cases.
- Umlaute in Use-Case-Namen als ae/ue-Schreibweise (Rendersicherheit); Akteursnamen
  mit Stereotyp <<externes System>> fuer Sekundaerakteure.

## Wichtige Modellierungsentscheidungen (Kurzfassung, Details in evaluation.md)
- 15 Use Cases (Mindestanforderung: 5), Systemgrenze "EasyLib", alle 5 Akteure ausserhalb.
- Primaerakteure links (Bibliothekar, Kunde, Buchhalter), Sekundaerakteure rechts
  (Verbundkatalog, Vernetzte Bibliotheken).
- Genau eine extend-Beziehung; auf weitere include/extend bewusst verzichtet
  (Prompt: nur wenn fachlich klar begruendbar).

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
- [ ] Commit: ergebnis(easylib/claude): use-case v1 + evaluation
