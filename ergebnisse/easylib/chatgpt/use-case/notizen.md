# Notizen: easylib / chatgpt / use-case

## Generierung v1

- Datum der Generierung: 2026-07-14
- KI: ChatGPT (Built-in Imagegen)
- Prompt: `prompts/use-case/easylib-v1.md`
- Vorhandenes Originalartefakt: `v1-direkt.png`
- Bildmetadaten: PNG, 1693 × 929 Pixel, SHA-256
  `95EBF2C2606414D2632CDF70B5CA7AFB0ECA50BB63B46E9EF0AC5EAB44529525`
- PlantUML-Code: fehlte im damaligen Direktbild-Arbeitsschritt; am 2026-07-14 nachgetragen,
  siehe Nachtrag unten.
- PlantUML-Rendering und Rendering-Tooling: nicht vorhanden.
- Generierungsverlauf: Der Inhalt von Basis- und Diagramm-Prompt wurde zu einer
  strukturierten Bildspezifikation normalisiert und in einem eigenständigen Imagegen-Aufruf
  ohne Referenzbilder ausgeführt. Das gespeicherte PNG ist eine unveränderte Kopie der
  direkten Modellausgabe.
- Modellierungsentscheidung im Generierungsprompt: „Buchdaten importieren“ wurde als
  optionale Erweiterung (`<<extend>>`) von „Exemplar einpflegen“ spezifiziert, weil beim
  Einpflegen wahlweise importiert oder manuell erfasst wird.
- Methodikabweichung: Die im Prompt vorgesehenen zwei Nachrichten mit zwischenzeitlichem
  Verständnis-Check wurden nicht getrennt ausgeführt. Die drei Systeme entstehen innerhalb
  derselben Codex-Aufgabe, aber jeweils in einem separaten Imagegen-Durchlauf ohne Bildkontext
  aus den anderen Systemen.

## Rohbeobachtungen zur Sichtprüfung am 2026-07-14

- Systemgrenze „EasyLib“ vollständig und eindeutig beschriftet.
- Bibliothekar, Kunde, Buchhalter, Verbundkatalog und vernetzte Bibliotheken stehen außerhalb
  der Systemgrenze.
- 17 Use-Case-Ellipsen vorhanden; Mindestanforderung erfüllt, aber die verlangten 15
  unterschiedlichen Use Cases wegen zwei Duplikaten verfehlt.
- „Bestand durchsuchen“ und „Standort und Status einsehen“ wurden je zweimal gezeichnet und
  durch eine unbeschriftete Volllinie verbunden, statt je einen gemeinsamen Use Case zu bilden.
- Die `<<extend>>`-Beziehung für den optionalen Katalogimport ist korrekt ausgerichtet und der
  Verbundkatalog ist mit „Buchdaten importieren“ verbunden.
- Die vernetzten Bibliotheken sind fälschlich mit „Leihfrist verlängern“ verbunden; die
  richtige Zuordnung zu „Bestand vernetzter Bibliotheken durchsuchen“ fehlt.
- „Kundendaten einsehen“ ist nicht erkennbar mit dem Bibliothekar verbunden.
- Mehrere Akteursassoziationen enden an Sammelpunkten neben den Figuren.
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

- `v1.puml` nachträglich anhand von `prompts/use-case/easylib-v1.md` und
  `lastenhefte/easylib.md` erzeugt; SHA-256:
  `E3E479C88BC42CA214B430B6D965333E21DD3D3A58FF6BA9FF48AE92EAD0541B`.
- Inhalt: fünf Akteure und 15 unterschiedliche Use Cases. Bestandssuche und Statuseinsicht
  sind jeweils gemeinsame Use Cases für Bibliothekar und Kunde; beide externen Systeme sind
  fachlich korrekt zugeordnet.
- „Buchdaten aus Verbundkatalog importieren“ erweitert „Exemplar einpflegen“ optional über
  `<<extend>>`. Die Annahme zur mehrdeutigen Leihfristverlängerung, die Bedingung der
  Kontolöschung und der Kundendatenschutz sind als Notizen dokumentiert.
- Statische Strukturprüfung erfolgreich: je ein `@startuml`/`@enduml`, ausgeglichene
  Klammern, fünf Akteure, 15 Use Cases und drei geschlossene Notizpaare.
- Kompilierung und Rendering nicht geprüft: lokal weder PlantUML-Kommando noch
  PlantUML-JAR vorhanden.
- Methodikabweichung: Code und Direktbild stammen aus getrennten Generierungsdurchläufen.
