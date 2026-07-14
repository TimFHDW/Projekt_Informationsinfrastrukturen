# Evaluation: easyscoot / chatgpt / sequenz

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easyscoot-v1.md` |
| Rendering-Weg | Direktbild: Built-in Imagegen; PlantUML-Rendering offen |

Skalen und Regeln: `evaluation/kriterien.md`. In dieser Zelle liegt bislang nur das
Direktbild vor; PlantUML-Code und -Rendering bleiben offen und werden nicht bewertet.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 4/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: für PlantUML offen.
- Direktes Bild – UML-Notation korrekt?: Akteur, Objekt-Lebenslinien,
  Aktivierungsbalken, synchrone Aufrufe und gestrichelte Antwortpfeile sind klar notiert.
  Ein lokaler Fehler besteht in einer zusätzlichen vorzeitigen Antwort
  `Fahrtzusammenfassung` auf `beendeNutzung(scooterId)`, obwohl der Systemaufruf danach
  weiterläuft und am Ende korrekt ein zweites Mal beantwortet wird. Durch Entfernen dieses
  einen Pfeils wäre die Aufruf-/Antwortstruktur konsistent.

## K2 – Inhaltliche Korrektheit — Score: offen (Direktbild: 4/5)

Abgleich mit `lastenhefte/easyscoot.md`:

- Nutzung beenden, E-Scooter sperren und auf `stehend` / `nichtInBenutzung` setzen,
  Fahrtdaten ermitteln, Preis extern berechnen lassen und die Zusammenfassung erstellen
  sind fachlich passend und in der geforderten Reihenfolge angeordnet.
- Dauer, Kilometer und Wattstunden werden an das Rechnungssystem übergeben; die
  Preisberechnung liegt damit korrekt außerhalb von EasyScoot. Es wurden keine
  Bezahlfunktion, Bewertung oder sonstigen fachfremden Funktionen ergänzt.
- Inhaltlicher Abzug: Eine `Fahrtzusammenfassung` wird bereits direkt nach der
  Statusaktualisierung an den Kunden zurückgegeben, also bevor Fahrtdaten und Preis
  vorliegen. Die zweite, abschließende Rückgabe ist dagegen korrekt.

## K3 – Vollständigkeit — Score: offen (Direktbild: 5/5)

- Mindestanforderung erfüllt (Aufrufe ≥ 5): ja; fünf synchrone Methodenaufrufe sind
  vorhanden.
- Alle geforderten Lebenslinien und Ablaufstationen sind enthalten. Die finale
  Fahrtzusammenfassung wird aus Dauer, Kilometern, Wattstunden und extern berechnetem Preis
  erstellt und an den Kunden zurückgegeben.
- Fehlende zentrale Elemente im Direktbild: keine.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: scharfes Querformat, gut getrennte Lebenslinien,
  große Beschriftungen, keine Überlappungen und keine abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar, da PlantUML-Code und -Rendering fehlen.

## Was hätten wir anders modelliert?

- Die vorzeitige Rückgabe der Fahrtzusammenfassung entfernen. Der Kunde sollte genau eine
  Antwort erhalten, nachdem Fahrtdaten und externer Preis vollständig vorliegen.

## Sonstige Beobachtungen

- Das Bild wurde als eigenständige, direkte Bildgenerierung ohne PlantUML- oder
  Bildreferenz erzeugt und unverändert gespeichert.
- Die zwei Prompt-Schritte wurden technisch zu einer strukturierten Bildspezifikation
  zusammengeführt; ein separater Verständnis-Check fand nicht statt.
