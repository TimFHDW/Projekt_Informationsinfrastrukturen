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

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easyride.png`)
- Erzeugt am 2026-07-07 (~17:25 CEST) in laufender Cowork-Session (Claude, im Auftrag von
  Lewin). Grundlage: Schritt-2-Vorgaben aus `prompts/use-case/easyride-v1.md` und das bereits
  abgelegte `v1.puml` als Modellbasis (Prompt-Regel: beide Ausgabeformen muessen inhaltlich
  uebereinstimmen).
- Tooling: Claude hat das Bild selbst gezeichnet (eigenes Python/Pillow-Zeichenskript der KI,
  Layout/Koordinaten von der KI bestimmt, KEINE PlantUML-Beteiligung). Skript wegen
  Sync-Latenz aus /tmp ausgefuehrt; Ablage per MD5-Vergleich + PIL-verify bestaetigt, Bild
  visuell geprueft (5 Use Cases, 2 Akteure, Systemgrenze "EasyRide", keine Kantenkreuzungen).
- Methodik-Einschraenkungen: (1) Bild nachtraeglich aus v1.puml abgeleitet statt im selben
  Generierungsdurchlauf -> inhaltliche Uebereinstimmung PlantUML vs. direkt ist
  konstruktionsbedingt und NICHT als unabhaengiger Befund fuer
  `vergleiche/plantuml-vs-direkt.md` verwertbar (dort nur Zeichenqualitaet/K4 vergleichen);
  (2) alle drei Use-Case-Bilder in einer Sitzung erzeugt -> moeglicher Struktur-Uebertrag
  zwischen den Systemen (identisches Layoutschema: UC-Spalte, Primaerakteure links,
  Sekundaerakteure rechts).
- Namensabweichung: AGENTS.md/DoD sieht `v1-direkt.png` vor; auf ausdruecklichen Wunsch von
  Lewin analog zu den Klassendiagramm-Zellen mit Systemnamen benannt
  (`v1-direkt-easyride.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] v1-direkt-easyride.png (direkt generiertes Bild) – nachgeliefert am 2026-07-07,
      siehe Nachtrag oben
- [ ] PlantUML rendern -> v1-plantuml.png/.svg; Renderweg hier notieren
- [ ] K1/K4 in evaluation.md finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] evaluation/ergebnismatrix.md aktualisieren
- [ ] Journal-Eintrag in dokumentation/vorgehen.md
- [ ] Commit: ergebnis(easyride/claude): use-case v1 + evaluation

## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1)
- Neue Dateien: `v2.puml` und `v2-direkt.png` (PNG ohne Systemnamen, wie bei den Klassendiagramm-/
  Aktivitaets-v2-Zellen). `v2-plantuml.png` steht aus – Renderer in dieser Session 403-gesperrt
  (npm/Maven/CDN); lokal nachrendern (z. B. IntelliJ-PlantUML-Plugin).
- Versionierung: v2 = ZWEITER Durchlauf mit unveraendertem Prompt v1 (Wunsch Tim) – Abweichung von
  „N = Prompt-Version"; als Durchlauf-Varianz lesen, nicht als Prompt-Iteration.
- Unabhaengigkeit: v1 dieser Zelle (`v1.puml`, `v1-direkt-easyride.png`) auf Wunsch von Tim BEWUSST
  NICHT eingesehen; Generierung allein aus `prompts/use-case/easyride-v1.md`. Einschraenkung: im
  Sitzungskontext waren Doku-/Journal-Eintraege mit v1-Bezuegen sichtbar -> kein vollstaendig
  isolierter Durchlauf.
- `v2.puml` und `v2-direkt.png` im SELBEN Durchlauf erzeugt (Bild nicht aus der puml abgeleitet);
  Direktbild via eigenem Use-Case-SVG-Generator -> librsvg/cairo -> PNG.
- Methodik-Abweichungen wie zuvor: keine frische Session; Zweischritt-Prompt nicht getrennt; alle
  drei v2-Use-Case-Bilder in einer Sitzung -> moeglicher Struktur-Uebertrag zwischen Systemen.
- Inhalt v2: Akteure Kunde (Fahrgast) und Fahrer ausserhalb der Systemgrenze „EasyRide"; genau 5
  Use Cases aus den abschliessenden Leistungslisten (Kunde: Fahrt buchen, Wartezeit abfragen,
  Restfahrzeit abfragen; Fahrer: naechsten Halt mit Fahrgastwechsel abfragen, Erreichen
  bestaetigen). Kein include/extend (nicht fachlich noetig).
- Noch offen (v2): `v2-plantuml.png` rendern; vollstaendige K1-K4-Bewertung.
