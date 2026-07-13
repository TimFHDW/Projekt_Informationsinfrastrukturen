# Notizen: easyride / chatgpt / klassendiagramm

## Generierung v1

- Datum: 2026-07-11
- KI/Werkzeug: ChatGPT/Codex, integriertes Imagegen-Werkzeug (Built-in-Modus)
- Promptgrundlage: `prompts/klassendiagramm/easyride-v1.md`
- Ergebnis: `v1-direkt-chatgpt.png`
- SHA-256: `4FD148B8E7BDF2C924134BDDBE328E1F00C9B8E5F58D93B5235ADCC15BFEE118`
- Eigenständiger Generierungsdurchlauf nur für EasyRide; kein Bild eines anderen Systems als Kontext verwendet.
- Methodikabweichung: Der zweistufige Textprompt wurde für das Bildwerkzeug zu einer strukturierten Bildspezifikation zusammengeführt; es gab keinen separaten Verständnis-Check. Nur das Direktbild wurde angefordert, kein PlantUML-Code.
- Dateinamensabweichung auf Nutzerwunsch: `v1-direkt-chatgpt.png` statt `v1-direkt.png`.
- Das generierte PNG wurde unverändert aus dem Imagegen-Ausgabeordner in die Ergebniszelle kopiert.

## Rohbeobachtungen

- Bild technisch vollständig, scharf und gut lesbar.
- Alle neun geforderten Klassen sowie Methoden und beide Constraints sichtbar.
- `{ordered}` an der Komposition Route–Routenhalt sichtbar.
- Fahrzeug fälschlich mit Routenhalt statt Route verbunden.
- Routenhalt fälschlich mit Verbindung statt Haltepunkt verbunden.
- Buchung–Fahrgast fehlt.

## Offene DoD-Punkte

- [x] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] Direktbild (`v1-direkt-chatgpt.png`)
- [x] `evaluation.md` (Direktbild bewertet, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert

## Nachtrag PlantUML am 2026-07-13

- `v1.puml` nachträglich anhand von `prompts/klassendiagramm/easyride-v1.md` erzeugt; SHA-256: `80FADF5A19AC1397BEB3F15B62CD6AB6C01D056C325060879E62714ECE9CD72B`.
- Methodikabweichung: Code und Direktbild stammen nicht aus demselben Generierungsdurchlauf; die sechs PUML-Dateien wurden in derselben Codex-Session erstellt.
- Statische Strukturprüfung erfolgreich: ein `@startuml`/`@enduml` und ausgeglichene Blockklammern.
- Kompilierung und Rendering nicht geprüft: lokal kein PlantUML vorhanden; Download von PlantUML 1.2026.3 wurde nicht freigegeben.
