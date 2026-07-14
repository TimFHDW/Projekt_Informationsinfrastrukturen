# Notizen: easyscoot / chatgpt / use-case

## Generierung v1

- Datum der Generierung: 2026-07-14
- KI: ChatGPT (Built-in Imagegen)
- Prompt: `prompts/use-case/easyscoot-v1.md`
- Vorhandenes Originalartefakt: `v1-direkt.png`
- Bildmetadaten: PNG, 1693 × 929 Pixel, SHA-256
  `73E1CCF02095A1505704194D0305CD2F3E437FB4071DC5AD6967F7B8D12CD3CC`
- PlantUML-Code: fehlte im damaligen Direktbild-Arbeitsschritt; am 2026-07-14 nachgetragen,
  siehe Nachtrag unten.
- PlantUML-Rendering und Rendering-Tooling: nicht vorhanden.
- Generierungsverlauf: Der Inhalt von Basis- und Diagramm-Prompt wurde zu einer
  strukturierten Bildspezifikation normalisiert und in einem eigenständigen Imagegen-Aufruf
  ohne Referenzbilder ausgeführt. Das gespeicherte PNG ist eine unveränderte Kopie der
  direkten Modellausgabe.
- Methodikabweichung: Die im Prompt vorgesehenen zwei Nachrichten mit zwischenzeitlichem
  Verständnis-Check wurden nicht getrennt ausgeführt. Die drei Systeme entstehen innerhalb
  derselben Codex-Aufgabe, aber jeweils in einem separaten Imagegen-Durchlauf ohne Bildkontext
  aus den anderen Systemen.

## Rohbeobachtungen zur Sichtprüfung am 2026-07-14

- Systemgrenze „EasyScoot“ vollständig und eindeutig beschriftet.
- Fünf Akteure stehen außerhalb der Systemgrenze.
- Elf Use Cases vorhanden; Mindestanforderung erfüllt.
- Kunde, Flottenmanager und Service-Mitarbeiter sind ihren Use Cases fachlich richtig
  zugeordnet.
- „Statusdaten übermitteln“ bildet die periodischen Mobilfunkmeldungen der E-Scooter-Software
  ab.
- Fehlerhafte Zuordnung rechts: „Nutzung beenden“ führt zur E-Scooter-Software statt zum
  Rechnungssystem.
- Fehlerhafte Zuordnung rechts: „Wartungsmodus beenden“ führt sichtbar zum Rechnungssystem
  statt zur E-Scooter-Software.
- „Wartungsmodus starten“ endet rechts in einer mehrdeutigen Linienstruktur.
- Mehrere Assoziationen berühren die Akteursfiguren nicht; links entstehen Linienfächer an
  Punkten neben den Akteuren.
- Alle Beschriftungen sind scharf und ohne sichtbare Schreibfehler; nichts ist abgeschnitten.

## Offene DoD-Punkte

- [x] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] `v1-direkt.png`
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert

## Nachtrag PlantUML am 2026-07-14

- `v1.puml` nachträglich anhand von `prompts/use-case/easyscoot-v1.md` und
  `lastenhefte/easyscoot.md` erzeugt; SHA-256:
  `869C7D168B0C8B0ADF6C6E07EDA100118DE6CAC15E35685D92B6D0453B75428F`.
- Inhalt: fünf Akteure, elf Use Cases und eindeutige Assoziationen. Rechnungssystem und
  E-Scooter-Software sind fachlich korrekt beteiligt; keine `include`-/`extend`-Beziehungen.
- Statische Strukturprüfung erfolgreich: je ein `@startuml`/`@enduml`, ausgeglichene
  Klammern, fünf Akteure, elf Use Cases und ein geschlossenes Notizpaar.
- Kompilierung und Rendering nicht geprüft: lokal weder PlantUML-Kommando noch
  PlantUML-JAR vorhanden.
- Methodikabweichung: Code und Direktbild stammen aus getrennten Generierungsdurchläufen.
