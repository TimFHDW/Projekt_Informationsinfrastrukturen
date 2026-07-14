# Evaluation: easyscoot / chatgpt / sequenz

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easyscoot-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. `v1.puml` liegt vor und wurde statisch geprüft;
Kompilierung und Rendering bleiben mangels lokalem PlantUML-Tool offen.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 4 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Fehlerliste: statische Prüfung unauffällig: je ein `@startuml`/`@enduml`, fünf synchrone
  Aufrufe und fünf Antworten, fünf `activate`/`deactivate`-Paare sowie ausgeglichene
  Klammern. Dies belegt nicht die Kompilierbarkeit.
- Direktes Bild – UML-Notation korrekt?: Akteur, Objekt-Lebenslinien,
  Aktivierungsbalken, synchrone Aufrufe und gestrichelte Antwortpfeile sind klar notiert.
  Ein lokaler Fehler besteht in einer zusätzlichen vorzeitigen Antwort
  `Fahrtzusammenfassung` auf `beendeNutzung(scooterId)`, obwohl der Systemaufruf danach
  weiterläuft und am Ende korrekt ein zweites Mal beantwortet wird. Durch Entfernen dieses
  einen Pfeils wäre die Aufruf-/Antwortstruktur konsistent.

## K2 – Inhaltliche Korrektheit — Score: PlantUML 5/5 · Direktbild 4/5

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
- PlantUML-Code: Die Nutzung wird beendet, der E-Scooter gesperrt und sein Fahr-/Leihstatus
  aktualisiert. Anschließend werden Fahrtdaten ermittelt, der Preis ausschließlich über
  `Rechnungssystem.preisBerechnen(fahrt: Fahrt)` berechnet und genau eine vollständige
  Zusammenfassung zurückgegeben. Keine inhaltlichen Fehler festgestellt.

## K3 – Vollständigkeit — Score: PlantUML 5/5 · Direktbild 5/5

- Mindestanforderung erfüllt (Aufrufe ≥ 5): ja; fünf synchrone Methodenaufrufe sind
  vorhanden.
- Alle geforderten Lebenslinien und Ablaufstationen sind enthalten. Die finale
  Fahrtzusammenfassung wird aus Dauer, Kilometern, Wattstunden und extern berechnetem Preis
  erstellt und an den Kunden zurückgegeben.
- Fehlende zentrale Elemente im Direktbild: keine.
- PlantUML-Code: fünf synchrone Aufrufe mit fünf Antworten, alle geforderten Lebenslinien
  und sämtliche Ablaufstationen einschließlich externer Preisberechnung vorhanden.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: 5, Befunde: gerendert; sehr sauber, Aktivierungsbalken und Notizen.
- Direktes Bild — Score: 5/5, Befunde: scharfes Querformat, gut getrennte Lebenslinien,
  große Beschriftungen, keine Überlappungen und keine abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Ein Layoutvergleich bleibt ohne Rendering offen. Inhaltlich sendet der PlantUML-Code die
  Fahrtzusammenfassung genau einmal und erst nach Fahrtdatenermittlung und Preisberechnung;
  damit vermeidet er den vorzeitigen doppelten Antwortpfeil des Direktbilds. Außerdem nutzt
  er die Klassendiagramm-Signatur `preisBerechnen(fahrt: Fahrt)`.

## Was hätten wir anders modelliert?

- Die vorzeitige Rückgabe der Fahrtzusammenfassung entfernen. Der Kunde sollte genau eine
  Antwort erhalten, nachdem Fahrtdaten und externer Preis vollständig vorliegen.

## Sonstige Beobachtungen

- Das Bild wurde als eigenständige, direkte Bildgenerierung ohne PlantUML- oder
  Bildreferenz erzeugt und unverändert gespeichert.
- Die zwei Prompt-Schritte wurden technisch zu einer strukturierten Bildspezifikation
  zusammengeführt; ein separater Verständnis-Check fand nicht statt.
- Der PlantUML-Code wurde nachträglich und damit nicht im selben Generierungsdurchlauf wie
  das Direktbild erzeugt. Fehlende Operationen sind entsprechend der Promptvorgabe als
  gedankliche Ergänzungen zum Klassendiagramm im Code ausgewiesen.
