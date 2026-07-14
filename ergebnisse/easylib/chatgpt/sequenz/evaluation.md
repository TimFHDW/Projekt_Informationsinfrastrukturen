# Evaluation: easylib / chatgpt / sequenz

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easylib-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. `v1.puml` liegt vor und wurde statisch geprüft;
Kompilierung und Rendering bleiben mangels lokalem PlantUML-Tool offen.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 4 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Fehlerliste: statische Prüfung unauffällig: je ein `@startuml`/`@enduml`, sechs synchrone
  Aufrufe und sechs Antworten, sechs `activate`/`deactivate`-Paare, eine
  `create participant`-Deklaration für `Ausleihe` sowie ausgeglichene Klammern. Dies belegt
  nicht die Kompilierbarkeit.
- Direktes Bild – UML-Notation korrekt?: Akteur, Objekt-Lebenslinien,
  Aktivierungsbalken, synchrone Aufrufe und gestrichelte Antwortpfeile sind klar notiert.
  Die Erzeugungsnachricht ist als `«create»` markiert, der Teilnehmerkopf und die
  gestrichelte Lebenslinie der `Ausleihe` beginnen jedoch bereits oben im Diagramm. Bei
  korrekter UML-Erzeugungsnotation müssten Kopf und Lebenslinie erst am Ziel der
  Create-Nachricht beginnen.

## K2 – Inhaltliche Korrektheit — Score: PlantUML 5/5 · Direktbild 5/5

Abgleich mit `lastenhefte/easylib.md`:

- Kunde und physisches Buchexemplar werden anhand ihrer IDs ermittelt; anschließend wird
  die Verfügbarkeit geprüft, eine Ausleihe mit Leihfrist angelegt und der Ausleihe- sowie
  Reservierungsstatus des Exemplars aktualisiert.
- Die Abschlussantwort geht an den Bibliothekar. Eine Notiz stellt ausdrücklich klar, dass
  das Exemplar und nicht das bibliografische Buch verliehen wird.
- Die Verfügbarkeitsbedingung ist vor der Erzeugung als Guard notiert. Es wurden keine
  fachfremden Funktionen ergänzt und keine inhaltlichen Fehler zum Lastenheft festgestellt.
- PlantUML-Code: Kunde und physisches Exemplar werden ID-basiert ermittelt, die
  Verfügbarkeit umfasst Leih- und Reservierungsstatus, die Ausleihe erhält eine Leihfrist
  und der Exemplarstatus wird aktualisiert. Werk-/Exemplartrennung und Annahme zur
  Leihfristverlängerung sind explizit notiert; keine inhaltlichen Fehler festgestellt.

## K3 – Vollständigkeit — Score: PlantUML 5/5 · Direktbild 5/5

- Mindestanforderung erfüllt (Aufrufe ≥ 5): ja; sechs synchrone Methodenaufrufe und sechs
  Antwortpfeile sind vorhanden.
- Alle geforderten Lebenslinien, die `create`-Nachricht, ID-basierte Ermittlung,
  Verfügbarkeitsprüfung, Leihfrist, Statusaktualisierung und Bestätigung sind enthalten.
- Fehlende zentrale Elemente im Direktbild: keine. Der zu frühe Beginn der
  Ausleihe-Lebenslinie ist unter K1 als Notationsfehler erfasst.
- PlantUML-Code: sechs synchrone Aufrufe mit sechs Antworten, alle geforderten
  Lebenslinien und Ablaufstationen vorhanden. `Ausleihe` wird per `create participant`
  unmittelbar an ihrer Erzeugungsnachricht eingeführt.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: 5, Befunde: gerendert; sehr sauber, inkl. create-Nachricht und Aktivierungsbalken.
- Direktes Bild — Score: 5/5, Befunde: scharfes Querformat, klare zeitliche Leserichtung,
  gut lesbare Beschriftungen, keine Überlappungen und keine abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Ein Layoutvergleich bleibt ohne Rendering offen. Inhaltlich beginnen Teilnehmerkopf und
  Lebenslinie der `Ausleihe` im PlantUML-Code erst an der Create-Nachricht; damit behebt der
  Code den zentralen Notationsfehler des Direktbilds. Beide Formen verleihen ausdrücklich
  das physische Exemplar und bilden denselben fachlichen Ablauf ab.

## Was hätten wir anders modelliert?

- Teilnehmerkopf und Lebenslinie der `Ausleihe` erst an der Create-Nachricht beginnen
  lassen. Für eine detailliertere Architektur könnten Kunde und Exemplar über eigene
  Repository-Lebenslinien anhand ihrer IDs geladen werden; der Prompt verlangt diese
  zusätzlichen Beteiligten jedoch nicht.

## Sonstige Beobachtungen

- Das Bild wurde als eigenständige, direkte Bildgenerierung ohne PlantUML- oder
  Bildreferenz erzeugt und unverändert gespeichert.
- Die zwei Prompt-Schritte wurden technisch zu einer strukturierten Bildspezifikation
  zusammengeführt; ein separater Verständnis-Check fand nicht statt.
- Der PlantUML-Code wurde nachträglich und damit nicht im selben Generierungsdurchlauf wie
  das Direktbild erzeugt. Fehlende Operationen sind entsprechend der Promptvorgabe als
  gedankliche Ergänzungen zum Klassendiagramm im Code ausgewiesen.
