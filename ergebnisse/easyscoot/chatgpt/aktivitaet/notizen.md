# Notizen: easyscoot / chatgpt / aktivitaet

## Generierung v1

- Datum der Generierung: 2026-07-10
- KI: ChatGPT
- Prompt: `prompts/aktivitaet/easyscoot-v1.md`
- Szenario: „E-Scooter ausleihen und nutzen“
- Vorhandenes Originalartefakt: `v1-direkt-chatgpt.png`
- PlantUML-Code: fehlt; wurde in diesem Arbeitsschritt bewusst noch nicht erzeugt.
- PlantUML-Rendering und Rendering-Tooling: nicht vorhanden.
- Methodikabweichung: Die drei Systeme wurden in derselben Chat-Session bearbeitet; die zwei Prompt-Schritte wurden nicht getrennt mit zwischenzeitlicher Bestätigung ausgeführt.
- Generierungsverlauf: Zunächst entstand eine gemeinsame Gesamtgrafik für alle Systeme; anschließend wurde EasyScoot eigenständig neu generiert. Bewertet wird ausschließlich die finale Einzelgrafik.
- Dateinamensabweichung: `v1-direkt-chatgpt.png` statt `v1-direkt.png`; das Original wurde unverändert belassen.

## Rohbeobachtungen zur Sichtprüfung am 2026-07-11

- Drei Swimlanes vorhanden: Kunde, EasyScoot-System und Rechnungssystem.
- Start- und Endknoten vorhanden.
- Mindestanforderung von fünf Aktivitäten deutlich erfüllt.
- Keine Entscheidung und keine alternativen, beschrifteten Entscheidungskanten vorhanden.
- Preisberechnung liegt korrekt in der Swimlane des Rechnungssystems.
- Ablaufproblem: Preisberechnung wird vor der Erfassung der preisrelevanten Nutzungsdaten angestoßen.
- „Nutzung beenden“ ist dem System statt dem Kunden zugeordnet.
- Gestrichelte Verbindungen zum Rechnungssystem sind semantisch nicht eindeutig.
- Bild ist scharf, vollständig und ohne Überlappungen lesbar.

## Offene DoD-Punkte

- [x] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] Direktbild (`v1-direkt-chatgpt.png`)
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert

## Nachtrag PlantUML am 2026-07-13

- `v1.puml` nachträglich anhand von `prompts/aktivitaet/easyscoot-v1.md` erzeugt; SHA-256: `469EBEA38E8A169779393966AA35F04897474C55F9B6CD2051226ABCE53DDF0F`.
- Methodikabweichung: Code und Direktbild stammen nicht aus demselben Generierungsdurchlauf; die sechs PUML-Dateien wurden in derselben Codex-Session erstellt.
- Statische Strukturprüfung erfolgreich: ein `@startuml`/`@enduml`, ausgeglichene Blockklammern, 1 `if`/1 `endif`.
- Kompilierung und Rendering nicht geprüft: lokal kein PlantUML vorhanden; Download von PlantUML 1.2026.3 wurde nicht freigegeben.
