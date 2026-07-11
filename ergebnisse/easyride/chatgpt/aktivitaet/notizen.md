# Notizen: easyride / chatgpt / aktivitaet

## Generierung v1

- Datum der Generierung: 2026-07-10
- KI: ChatGPT
- Prompt: `prompts/aktivitaet/easyride-v1.md`
- Szenario: „Kunde bucht eine Fahrt“
- Vorhandenes Originalartefakt: `v1-direkt-chatgpt.png`
- PlantUML-Code: fehlt; wurde in diesem Arbeitsschritt bewusst noch nicht erzeugt.
- PlantUML-Rendering und Rendering-Tooling: nicht vorhanden.
- Methodikabweichung: Die drei Systeme wurden in derselben Chat-Session bearbeitet; die zwei Prompt-Schritte wurden nicht getrennt mit zwischenzeitlicher Bestätigung ausgeführt.
- Generierungsverlauf: Zunächst entstand eine gemeinsame Gesamtgrafik für alle Systeme; anschließend wurde EasyRide eigenständig neu generiert. Bewertet wird ausschließlich die finale Einzelgrafik.
- Dateinamensabweichung: `v1-direkt-chatgpt.png` statt `v1-direkt.png`; das Original wurde unverändert belassen.

## Rohbeobachtungen zur Sichtprüfung am 2026-07-11

- Zwei Swimlanes vorhanden: Kunde und EasyRide-System.
- Start- und Endknoten vorhanden.
- Neun nummerierte Schritte; die Mindestanforderung von fünf Aktivitäten ist erfüllt.
- Eine beschriftete Entscheidung mit den Ausgängen Ja/Nein vorhanden.
- Geforderte zweite Entscheidung fehlt.
- Alternative „Route erweitern / neue Route anlegen“ und Kapazitätsprüfung sind enthalten.
- Alternative Zweige werden ohne expliziten Merge-Knoten zusammengeführt.
- Bild ist scharf, vollständig und ohne Überlappungen lesbar.

## Offene DoD-Punkte

- [ ] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] Direktbild (`v1-direkt-chatgpt.png`)
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert
