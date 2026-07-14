# Notizen: easylib / claude / klassendiagramm (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~20:10 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Tim
- Prompt: `prompts/klassendiagramm/easylib-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm).
  Der Prompt speist die KI mit einer Paraphrase der Systembeschreibung.
- Referenz fuer die Evaluation (K2/K3): `lastenhefte/easylib.md` (offiziell, am 2026-07-06 aus
  OOSE-I Kapitel 4, Folien 180–183, transkribiert). Bei Generierung existierte diese Datei noch
  nicht; sie wurde nachtraeglich angelegt und das Diagramm dagegen geprueft.

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Die Generierung erfolgte in einer laufenden
   Cowork-Session mit erheblichem Vorkontext (zuvor u. a. EasyRide-/EasyScoot-Prompts
   erstellt und Repo-Regeln gelesen). Moeglicher Kontext-Einfluss („context bleed").
   -> Fuer den belastbaren KI-/System-Vergleich in einer frischen Session reproduzieren.
2. Zweistufiger Prompt nicht getrennt ausgefuehrt: Der in `easylib-v1.md` vorgesehene
   Ablauf (Schritt 1 senden, Verstaendnis-Check abwarten, dann Schritt 2) wurde nicht als
   zwei separate Nachrichten durchlaufen; das Diagramm wurde direkt als Ergebnis erzeugt.
3. Nur PlantUML-Form: Die vom Prompt zusaetzlich geforderte „direkt gezeichnete" Bildform
   (`v1-direkt.png`) wurde NICHT erzeugt. Damit ist die Zelle DoD-seitig unvollstaendig.

## Nachtraegliche Pruefung gegen offizielles Lastenheft (2026-07-06)
- `v1.puml` Element fuer Element gegen `lastenhefte/easylib.md` abgeglichen.
- Ergebnis: inhaltlich deckungsgleich; KEINE Korrektur noetig. `v1.puml` bleibt als
  Original-KI-Ausgabe unveraendert (Regel 7). Etwaige spaetere Renderkorrekturen kaemen in
  `v1-korrigiert.puml`, Begruendung hier.
- Zwei bewusst dokumentierte Nuancen (siehe evaluation.md K2):
  (a) Leihfrist-Verlaengerung: Modell nimmt die Gegenrichtung zur (unplausiblen) woertlichen
      Lastenheft-Formulierung an – als Notiz im Diagramm festgehalten.
  (b) Ausleihe/Reservierung auf Exemplar- bzw. Medium-Ebene (also auch fuer Hoerbuecher),
      waehrend das Lastenheft sprachlich „Buchexemplar"/„ein Buch" nutzt.

## Rendering / Tooling
- In dieser Umgebung war kein PlantUML-Rendering moeglich (kein lokales plantuml.jar; externer
  Download blockiert). Daher fehlt `v1-plantuml.png/.svg`; K1 (Syntax) und K4 (Lesbarkeit)
  sind noch nicht final bewertet. Renderweg des Teams festlegen und hier nachtragen.

## Wichtige Modellierungsentscheidungen (Kurzfassung, Begruendung in evaluation.md)
- Abstrakte Oberklasse `Medium` (= Werk-Ebene) mit `Buch`/`Hoerbuch` als Unterklassen.
- `Ausleihe` -> `Exemplar`; `Reservierung` -> `Medium`.
- `Autor` eigene Klasse, 1..*; `Genre` Enum mit exakt 9 Werten.
- Bibliothekar/Buchhalter als Akteure (Use-Case), nicht als Fachklassen.
- Externe Systeme `Verbundkatalog` und „Vernetzte Bibliothek" als «external system» angedeutet.
- Anschrift/Standort/Bibliotheksausweis inline modelliert (Alternativen in evaluation.md).

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easylib.png`)
- Erzeugt am 2026-07-07 (~18:45 CEST) in laufender Cowork-Session (Claude, im Auftrag von
  Linus). Grundlage: Schritt-2-Vorgaben aus `prompts/klassendiagramm/easylib-v1.md` und das
  bereits abgelegte `v1.puml` als Modellbasis (Prompt-Regel: beide Ausgabeformen muessen
  inhaltlich uebereinstimmen).
- Tooling: Claude hat das Bild selbst gezeichnet (eigenes Python/Pillow-Zeichenskript der KI,
  Layout und Koordinaten von der KI bestimmt) – KEINE PlantUML-Beteiligung. PNG 3800x2640 px.
- Methodik-Abweichungen: (1) erneut keine frische, isolierte Session; (2) Bild nicht im selben
  Durchlauf wie der PlantUML-Code entstanden, sondern nachtraeglich aus `v1.puml` abgeleitet –
  die inhaltliche Uebereinstimmung PlantUML vs. direkt ist damit konstruktionsbedingt und
  NICHT als unabhaengiger Befund fuer `vergleiche/plantuml-vs-direkt.md` verwertbar (dort nur
  Zeichenqualitaet/K4 vergleichen); (3) alle drei Klassendiagramm-Bilder in einer Sitzung
  erzeugt -> moeglicher Struktur-Uebertrag zwischen den Systemen.
- Namensabweichung: AGENTS.md/DoD sieht `v1-direkt.png` vor; auf ausdruecklichen Wunsch von
  Linus mit Systemnamen benannt (`v1-direkt-easylib.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] `v1-direkt-easylib.png` (direkt generiertes Bild) – nachgeliefert am 2026-07-07,
      siehe Nachtrag oben
- [ ] PlantUML rendern -> `v1-plantuml.png/.svg`; Renderweg hier notieren
- [ ] K1/K4 in `evaluation.md` finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] Commit: `ergebnis(easylib/claude): klassendiagramm v1 + evaluation`

## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1)

- Neue Dateien: `v2.puml`, `v2-direkt.png` und `v2-plantuml.png` (PNG-Benennung ohne
  Systemnamen, wie bei den Aktivitaets-Zellen; Wunsch Lewin).
- Versionierung: v2 bezeichnet einen ZWEITEN Generierungsdurchlauf mit unveraendertem
  Prompt v1 (auf Wunsch von Lewin, analog zum aktivitaet-v2-Durchlauf vom 14.07.) -
  Abweichung von der Konvention "N = Prompt-Version" (ergebnisse/README.md); fuer
  Vergleiche als Durchlauf-Varianz lesen, nicht als Prompt-Iteration.
- Generierung am 2026-07-14 (~16:35-17:10 CEST) in laufender Cowork-Session (Claude, im
  Auftrag von Lewin); Diagramme direkt in den DoD-Zellen abgelegt.
- Direktbild `v2-direkt.png`: von Claude selbst gezeichnet (eigenes Python/Pillow-
  Zeichenskript, Layout/Koordinaten von der KI bestimmt, KEINE PlantUML-Beteiligung);
  im SELBEN Durchlauf wie `v2.puml` erzeugt (nicht nachtraeglich abgeleitet), beide
  Formen stammen aus demselben Modell -> der inhaltliche Vergleich PlantUML vs. direkt
  ist fuer v2 weiterhin konstruktionsbedingt gleich, verwertbar ist v. a. K4.
- Unabhaengigkeit: `v1.puml` dieser Zelle wurde vor der v2-Generierung bewusst NICHT
  eingesehen; im Sitzungskontext waren allerdings Journal-Eintraege mit
  v1-Kurzbeschreibungen sichtbar -> kein vollstaendig unabhaengiger Durchlauf.
- Methodik-Abweichungen wie bei v1: keine frische isolierte Session; Zweischritt-Prompt
  nicht als getrennte Nachrichten; alle drei v2-Klassendiagramme in einer Sitzung ->
  moeglicher Struktur-Uebertrag zwischen den Systemen.
- Rendering: `v2-plantuml.png` am 2026-07-14 in der Cowork-Sandbox gerendert -
  plantuml.jar 1.2019.06 aus dem npm-Paket node-plantuml (npm in dieser Session wieder
  erreichbar, jar-Direktdownload weiterhin 403; Team-Renderweg vom 06.07.). `v2.puml`
  kompilierte fehlerfrei, keine Korrektur, kein `v2-korrigiert.puml`. PNGs per MD5 +
  PIL-verify geprueft, alle drei Direktbilder visuell abgenommen.
- Inhaltlich v2 (Kurzueberblick): Abstrakte Oberklasse `Medium` (Titel, Verlag, Auflage, Erscheinungsdatum,
  ISBN, Genre) mit `Buch` (seitenzahl) und `Hoerbuch` (anzahlDatentraeger,
  spiellaengeMinuten); `Exemplar` getrennt vom Werk (id, etage, regalnummer);
  `Autor` mit optionalen Attributen [0..1], Assoziation 1..*; `Genre`-Enum mit exakt
  9 Werten; `Ausleihe` am Exemplar, `Reservierung` am Medium (Ebenen-Notiz);
  Leihfrist-Mehrdeutigkeit als Constraint + explizite Annahme gegen den Wortlaut;
  Bibliothekar/Buchhalter als Akteure begruendet (keine Klassen) - ihre Funktionen
  buendelt die Systemklasse `EasyLib` «system» (Suche, Ein-/Auspflegen, Verleihen,
  Rueckgabe, Ueberfaelligen-Liste); Schnittstellen `Verbundkatalog` und
  `VernetzteBibliothek` mit Abhaengigkeiten; NEU: `Bibliotheksausweis` als eigene
  1:1-Klasse zum Kunden (Kunden-ID + Lichtbild abgedruckt).
- Annahmen der KI in diesem Durchlauf: ISBN auch fuer Hoerbuecher als gemeinsames Merkmal (Prompt zaehlt sie zu den
  gemeinsamen bibliografischen Merkmalen); Standort als zwei Attribute statt eigener
  Wertklasse; Datentyp `Bild` (lichtbild) nicht weiter modelliert; `kundenId` beim
  Kunden gefuehrt, auf dem Ausweis nur abgedruckt; Leihfrist als Datum.
- Sichtbare Durchlauf-Varianz gegenueber v1 (erst NACH der Generierung abgeglichen):
  v1 modellierte Bibliotheksausweis und Standort inline und kannte keine
  Systemklasse; v2 fuehrt `Bibliotheksausweis` als eigene 1:1-Klasse und die
  Systemklasse `EasyLib` als Traeger der Bibliothekars-/Buchhalter-Funktionen ein
  (deckt sich mit den in der v1-evaluation.md notierten Alternativen - dieser Abschnitt
  wurde erst NACH der v2-Generierung gelesen). Kern (Medium-Vererbung, Werk/Exemplar-
  Trennung, Genre-Enum, Ebenen-Entscheidung, Leihfrist-Annahme) stabil.
- Noch offen (v2): vollstaendige K2-K4-Bewertung in `evaluation.md`; Commit macht Lewin
  selbst (ausdruecklicher Wunsch, nichts committet).
