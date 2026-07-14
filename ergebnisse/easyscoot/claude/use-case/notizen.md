# Notizen: easyscoot / claude / use-case (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, nachmittags (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Alex
- Prompt: `prompts/use-case/easyscoot-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer K2/K3: `lastenhefte/easyscoot.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session, in der zuvor
   die Zellen easylib/claude/use-case und easyride/claude/use-case erstellt wurden ->
   moeglicher Kontext-Einfluss ("context bleed"), z. B. gleiche Skinparam-/Layout-Muster
   und Stereotyp-Schreibweise <<externes System>>. Fuer belastbaren Vergleich in
   frischer Session reproduzieren.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check
   ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (v1-direkt.png) fehlt.
4. Review-Schritt: Entwurf wurde Alex vor dem Ablegen gezeigt und freigegeben; die
   KI-Ausgabe selbst blieb dabei unveraendert.

## Annahmen der KI bei der Generierung
- "E-Scooter buchen und freischalten" als EIN Use Case (Prompt-Wortlaut; am Standort
  ein zusammenhaengender Vorgang aus Kundensicht).
- "Statusdaten uebermitteln" als zusaetzlicher Use Case mit dem E-Scooter als
  initiierendem (Primaer-)Akteur: die zyklische Meldung von Position, Ladezustand und
  Fahrstatus ist im Lastenheft explizit gefordert und eine Leistung des Systems
  (Entgegennahme/Speicherung), auch ohne menschlichen Akteur.
- Kein include/extend: gefilterte Liste (<= 50 %) als eigener Use Case statt
  <<extend>> von "Liste einsehen" - Lastenheft fuehrt sie als eigene Leistung;
  im Zweifel weggelassen (Prompt-Vorgabe).
- Rechnungssystem nur an "Nutzung beenden" beteiligt (Preisberechnung fuer die
  Fahrtzusammenfassung); keine eigene Bezahlfunktion modelliert.
- Wartungsmodus starten/beenden als zwei Use Cases (zwei getrennte Ausloesungen mit
  unterschiedlicher Wirkung: Ab- vs. Anmeldung des Scooters).
- Ladestationen sind Orte, keine Akteure; "E-Scooter zu Ladestation bringen" ist eine
  physische Taetigkeit ausserhalb des Softwaresystems und daher kein Use Case.
- Umlaute in Bezeichnern als ae/ue/ss-Schreibweise (Rendersicherheit); "<=" statt
  Unicode-Zeichen.

## Wichtige Modellierungsentscheidungen (Kurzfassung, Details in evaluation.md)
- 11 Use Cases (Mindestanforderung: 5), Systemgrenze "EasyScoot", alle 5 Akteure
  ausserhalb.
- "Liste aller E-Scooter einsehen" gemeinsam fuer Flottenmanager und
  Service-Mitarbeiter (ein Use Case, zwei Akteure).
- Sekundaerakteure: E-Scooter an UC3/UC4/UC7/UC8, Rechnungssystem an UC4;
  E-Scooter zusaetzlich Initiator von UC11.
- Keine include/extend-Beziehungen (begruendet, s. o.).

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich: Download der plantuml.jar
  weiterhin blockiert (versucht: GitHub Releases, 2026-07-06). Daher fehlt
  v1-plantuml.png/.svg; K1/K4 offen. Syntax nur per Sichtpruefung
  (@startuml/@enduml, rectangle-Block, Alias-Referenzen).
- Renderweg des Teams festlegen und hier nachtragen.

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easyscoot.png`)
- Erzeugt am 2026-07-07 (~17:25 CEST) in laufender Cowork-Session (Claude, im Auftrag von
  Lewin). Grundlage: Schritt-2-Vorgaben aus `prompts/use-case/easyscoot-v1.md` und das bereits
  abgelegte `v1.puml` als Modellbasis (Prompt-Regel: beide Ausgabeformen muessen inhaltlich
  uebereinstimmen).
- Tooling: Claude hat das Bild selbst gezeichnet (eigenes Python/Pillow-Zeichenskript der KI,
  Layout/Koordinaten von der KI bestimmt, KEINE PlantUML-Beteiligung). Skript wegen
  Sync-Latenz aus /tmp ausgefuehrt; Ablage per MD5-Vergleich + PIL-verify bestaetigt, Bild
  visuell geprueft (11 Use Cases, 5 Akteure inkl. zweier Sekundaerakteure mit Stereotyp
  «externes System», Systemgrenze "EasyScoot").
- Methodik-Einschraenkungen: (1) Bild nachtraeglich aus v1.puml abgeleitet statt im selben
  Generierungsdurchlauf -> inhaltliche Uebereinstimmung PlantUML vs. direkt ist
  konstruktionsbedingt und NICHT als unabhaengiger Befund fuer
  `vergleiche/plantuml-vs-direkt.md` verwertbar (dort nur Zeichenqualitaet/K4 vergleichen);
  (2) alle drei Use-Case-Bilder in einer Sitzung erzeugt -> moeglicher Struktur-Uebertrag
  zwischen den Systemen (identisches Layoutschema: UC-Spalte, Primaerakteure links,
  Sekundaerakteure rechts).
- Namensabweichung: AGENTS.md/DoD sieht `v1-direkt.png` vor; auf ausdruecklichen Wunsch von
  Lewin analog zu den Klassendiagramm-Zellen mit Systemnamen benannt
  (`v1-direkt-easyscoot.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] v1-direkt-easyscoot.png (direkt generiertes Bild) – nachgeliefert am 2026-07-07,
      siehe Nachtrag oben
- [ ] PlantUML rendern -> v1-plantuml.png/.svg; Renderweg hier notieren
- [ ] K1/K4 in evaluation.md finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] evaluation/ergebnismatrix.md aktualisieren
- [ ] Journal-Eintrag in dokumentation/vorgehen.md
- [ ] Commit: ergebnis(easyscoot/claude): use-case v1 + evaluation

## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1)
- Neue Dateien: `v2.puml` und `v2-direkt.png` (PNG ohne Systemnamen). `v2-plantuml.png` steht aus –
  Renderer in dieser Session 403-gesperrt; lokal nachrendern.
- Versionierung: v2 = ZWEITER Durchlauf mit unveraendertem Prompt v1 (Wunsch Tim) – Durchlauf-
  Varianz, nicht Prompt-Iteration.
- Unabhaengigkeit: v1 dieser Zelle (`v1.puml`, `v1-direkt-easyscoot.png`) auf Wunsch von Tim BEWUSST
  NICHT eingesehen; Generierung allein aus `prompts/use-case/easyscoot-v1.md`. Einschraenkung:
  Sitzungskontext mit v1-Bezuegen sichtbar -> kein vollstaendig isolierter Durchlauf.
- `v2.puml` und `v2-direkt.png` im SELBEN Durchlauf (Bild nicht aus puml abgeleitet); Direktbild via
  Use-Case-SVG-Generator -> librsvg/cairo.
- Methodik-Abweichungen wie zuvor (keine frische Session; kein getrennter Zweischritt-Prompt; alle
  drei v2-UC-Bilder in einer Sitzung).
- Inhalt v2: Akteure Kunde/Flottenmanager/Service-Mitarbeiter (primaer) + E-Scooter (Mobilfunk) und
  Rechnungssystem (Sekundaerakteure) ausserhalb „EasyScoot"; 10 Use Cases. „Liste aller E-Scooter
  einsehen" von Flottenmanager UND Service geteilt; Rechnungssystem an „Nutzung beenden", E-Scooter
  an Abfrage/Wartungsmodus. Kein include/extend.
- Noch offen (v2): `v2-plantuml.png` rendern; vollstaendige K1-K4-Bewertung.
