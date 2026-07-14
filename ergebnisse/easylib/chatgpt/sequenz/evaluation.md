# Evaluation: easylib / chatgpt / sequenz

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easylib-v1.md` |
| Rendering-Weg | Direktbild: Built-in Imagegen; PlantUML-Rendering offen |

Skalen und Regeln: `evaluation/kriterien.md`. In dieser Zelle liegt bislang nur das
Direktbild vor; PlantUML-Code und -Rendering bleiben offen und werden nicht bewertet.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 4/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: für PlantUML offen.
- Direktes Bild – UML-Notation korrekt?: Akteur, Objekt-Lebenslinien,
  Aktivierungsbalken, synchrone Aufrufe und gestrichelte Antwortpfeile sind klar notiert.
  Die Erzeugungsnachricht ist als `«create»` markiert, der Teilnehmerkopf und die
  gestrichelte Lebenslinie der `Ausleihe` beginnen jedoch bereits oben im Diagramm. Bei
  korrekter UML-Erzeugungsnotation müssten Kopf und Lebenslinie erst am Ziel der
  Create-Nachricht beginnen.

## K2 – Inhaltliche Korrektheit — Score: offen (Direktbild: 5/5)

Abgleich mit `lastenhefte/easylib.md`:

- Kunde und physisches Buchexemplar werden anhand ihrer IDs ermittelt; anschließend wird
  die Verfügbarkeit geprüft, eine Ausleihe mit Leihfrist angelegt und der Ausleihe- sowie
  Reservierungsstatus des Exemplars aktualisiert.
- Die Abschlussantwort geht an den Bibliothekar. Eine Notiz stellt ausdrücklich klar, dass
  das Exemplar und nicht das bibliografische Buch verliehen wird.
- Die Verfügbarkeitsbedingung ist vor der Erzeugung als Guard notiert. Es wurden keine
  fachfremden Funktionen ergänzt und keine inhaltlichen Fehler zum Lastenheft festgestellt.

## K3 – Vollständigkeit — Score: offen (Direktbild: 5/5)

- Mindestanforderung erfüllt (Aufrufe ≥ 5): ja; sechs synchrone Methodenaufrufe und sechs
  Antwortpfeile sind vorhanden.
- Alle geforderten Lebenslinien, die `create`-Nachricht, ID-basierte Ermittlung,
  Verfügbarkeitsprüfung, Leihfrist, Statusaktualisierung und Bestätigung sind enthalten.
- Fehlende zentrale Elemente im Direktbild: keine. Der zu frühe Beginn der
  Ausleihe-Lebenslinie ist unter K1 als Notationsfehler erfasst.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: scharfes Querformat, klare zeitliche Leserichtung,
  gut lesbare Beschriftungen, keine Überlappungen und keine abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar, da PlantUML-Code und -Rendering fehlen.

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
