# Notizen: easyride / chatgpt / use-case

## Generierung v1

- Datum der Generierung: 2026-07-14
- KI: ChatGPT (Built-in Imagegen)
- Prompt: `prompts/use-case/easyride-v1.md`
- Vorhandenes Originalartefakt: `v1-direkt.png`
- Bildmetadaten: PNG, 1693 × 929 Pixel, SHA-256
  `3B3844C09278AEA9D3FEB99B67D741A48C067DB890CA2C95D53314DCA96FA108`
- PlantUML-Code: fehlt; der Auftrag umfasste die noch fehlenden Direktbilder.
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

- Systemgrenze „EasyRide“ vollständig und eindeutig beschriftet.
- Beide Akteure stehen außerhalb der Systemgrenze.
- Genau fünf Use Cases; die Mindestanforderung ist erfüllt.
- Kunde (Fahrgast) ist den drei Kundenfunktionen, Fahrer den zwei Fahrerfunktionen
  inhaltlich richtig zugeordnet.
- Keine zusätzlichen internen oder erfundenen Use Cases und keine unbegründeten
  `include`-/`extend`-Beziehungen.
- Assoziationslinien enden mit kleinen Abständen vor den Akteursfiguren; die Zuordnung bleibt
  durch die räumliche Anordnung eindeutig.
- Scharfe Beschriftungen, keine Überlappungen oder abgeschnittenen Elemente.

## Offene DoD-Punkte

- [ ] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] `v1-direkt.png`
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert

