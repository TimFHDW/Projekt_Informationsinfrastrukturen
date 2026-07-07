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

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easylib.png`)
- Erzeugt am 2026-07-07 (~17:25 CEST) in laufender Cowork-Session (Claude, im Auftrag von
  Lewin). Grundlage: Schritt-2-Vorgaben aus `prompts/use-case/easylib-v1.md` und das bereits
  abgelegte `v1.puml` als Modellbasis (Prompt-Regel: beide Ausgabeformen muessen inhaltlich
  uebereinstimmen).
- Tooling: Claude hat das Bild selbst gezeichnet (eigenes Python/Pillow-Zeichenskript der KI,
  Layout/Koordinaten von der KI bestimmt, KEINE PlantUML-Beteiligung). Skript wegen
  Sync-Latenz aus /tmp ausgefuehrt; Ablage per MD5-Vergleich + PIL-verify bestaetigt, Bild
  visuell geprueft (15 Use Cases, 5 Akteure inkl. zweier Sekundaerakteure mit Stereotyp
  «externes System», Systemgrenze "EasyLib", extend-Pfeil UC2 -> UC1 mit «extend»-Label).
- Methodik-Einschraenkungen: (1) Bild nachtraeglich aus v1.puml abgeleitet statt im selben
  Generierungsdurchlauf -> inhaltliche Uebereinstimmung PlantUML vs. direkt ist
  konstruktionsbedingt und NICHT als unabhaengiger Befund fuer
  `vergleiche/plantuml-vs-direkt.md` verwertbar (dort nur Zeichenqualitaet/K4 vergleichen);
  (2) alle drei Use-Case-Bilder in einer Sitzung erzeugt -> moeglicher Struktur-Uebertrag
  zwischen den Systemen (identisches Layoutschema: UC-Spalte, Primaerakteure links,
  Sekundaerakteure rechts).
- Namensabweichung: AGENTS.md/DoD sieht `v1-direkt.png` vor; auf ausdruecklichen Wunsch von
  Lewin analog zu den Klassendiagramm-Zellen mit Systemnamen benannt
  (`v1-direkt-easylib.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] v1-direkt-easylib.png (direkt generiertes Bild) – nachgeliefert am 2026-07-07,
      siehe Nachtrag oben
- [ ] PlantUML rendern -> v1-plantuml.png/.svg; Renderweg hier notieren
- [ ] K1/K4 in evaluation.md finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] evaluation/ergebnismatrix.md aktualisieren
- [ ] Journal-Eintrag in dokumentation/vorgehen.md
- [ ] Commit: ergebnis(easylib/claude): use-case v1 + evaluation
