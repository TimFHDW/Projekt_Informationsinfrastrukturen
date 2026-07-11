# Notizen: easylib / chatgpt / aktivitaet

## Generierung v1

- Datum der Generierung: 2026-07-10
- KI: ChatGPT
- Prompt: `prompts/aktivitaet/easylib-v1.md`
- Szenario: „Bibliothekar pflegt ein neues Buchexemplar ein“
- Vorhandenes Originalartefakt: `v1-direkt-chatgpt.png`
- PlantUML-Code: fehlt; wurde in diesem Arbeitsschritt bewusst noch nicht erzeugt.
- PlantUML-Rendering und Rendering-Tooling: nicht vorhanden.
- Methodikabweichung: Die drei Systeme wurden in derselben Chat-Session bearbeitet; die zwei Prompt-Schritte wurden nicht getrennt mit zwischenzeitlicher Bestätigung ausgeführt.
- Generierungsverlauf: Nach der gemeinsamen Gesamtgrafik wurde EasyLib zunächst versehentlich erneut zusammen mit EasyScoot ausgegeben und danach allein neu generiert. Bewertet wird ausschließlich die finale Einzelgrafik.
- Dateinamensabweichung: `v1-direkt-chatgpt.png` statt `v1-direkt.png`; das Original wurde unverändert belassen.

## Rohbeobachtungen zur Sichtprüfung am 2026-07-11

- Nur eine Swimlane „Bibliothekar“ vorhanden; die geforderten Lanes EasyLib-System und Verbundkatalog fehlen.
- Start- und Endknoten vorhanden.
- Mindestanforderung von fünf Aktivitäten deutlich erfüllt.
- Zwei Entscheidungen mit beschrifteten Ja-/Nein-Ausgängen vorhanden.
- Beide Zweige der Importentscheidung werden wieder zusammengeführt.
- Werk und Exemplar werden unterschieden; eindeutige ID sowie Etage und Regalnummer sind enthalten.
- Alternative Zweige werden ohne explizite Merge-Knoten zusammengeführt.
- „ISBN bzw. Buchdaten erfassen“ vor der Katalogabfrage vermischt Suchdaten mit der späteren manuellen Vollerfassung.
- Bild ist scharf, vollständig und ohne Überlappungen lesbar.

## Offene DoD-Punkte

- [ ] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] Direktbild (`v1-direkt-chatgpt.png`)
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert
