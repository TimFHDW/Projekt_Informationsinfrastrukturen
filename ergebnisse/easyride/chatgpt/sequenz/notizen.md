# Notizen: easyride / chatgpt / sequenz

## Generierung v1

- Datum der Generierung: 2026-07-14
- KI: ChatGPT/Codex, Built-in Imagegen
- Prompt: `prompts/sequenz/easyride-v1.md`
- Szenario: „Fahrer bestätigt das Erreichen eines Haltepunkts“
- Originalartefakt: `v1-direkt.png`
- Bilddaten: 1693 × 929 px, 1.014.453 Bytes
- SHA-256: `286E00ED674445064040B31DB2A1F4D91D4ED2F3B3EA5CA9EE25365F1EB81381`
- Generierungsweg: eigenständiger Built-in-Imagegen-Aufruf ohne Referenzbild; das zuerst
  erzeugte PNG wurde unverändert aus dem Imagegen-Ausgabeordner in die DoD-Zelle kopiert.
- Methodikabweichung: Schritt 1 und Schritt 2 der Promptdatei wurden für das Bild in einer
  strukturierten Generierungsanweisung zusammengeführt; der vorgesehene Verständnis-Check
  zwischen zwei Nachrichten entfiel.
- PlantUML-Code und PlantUML-Rendering: in diesem Arbeitsschritt nicht erzeugt.

## Rohbeobachtungen zur Sichtprüfung

- Fünf synchrone Methodenaufrufe mit jeweils einem gestrichelten Antwortpfeil vorhanden.
- Fahrer ist als Akteur dargestellt; Lebenslinien und Aktivierungsbalken sind klar erkennbar.
- Ablaufkern des Lastenhefts und Rückgabe des nächsten Haltepunkts samt Fahrgastnamen
  vorhanden.
- `Betroffene Fahrgäste` ist eine zusätzliche, ungenutzte Lebenslinie.
- Fahrgastwechsel wird vor der Ermittlung des nächsten Haltepunkts und mit der aktuellen
  `haltepunktId` abgefragt; dadurch bleibt der Bezug zum nächsten Halt unscharf.
- Bild ist scharf, vollständig und ohne Überlappungen lesbar.

## Offene DoD-Punkte

- [x] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] `v1-direkt.png`
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert

## Nachtrag PlantUML am 2026-07-14

- `v1.puml` nachträglich anhand von `prompts/sequenz/easyride-v1.md`, dem Lastenheft und
  dem vorhandenen ChatGPT-Klassendiagramm erzeugt; SHA-256:
  `E8701E8CEE519DFDB4D79DF2548B06EA08051C0523BA162962BFA9AED01CE950`.
- Methodikabweichung: PlantUML-Code und Direktbild stammen nicht aus demselben
  Generierungsdurchlauf; für jedes System wird der Code dennoch separat ohne Bildreferenz
  erstellt.
- Namenskonsistenz: `Fahrer`, `Route`, `Routenhalt`, `Fahrt` und
  `restfahrzeitBerechnen` aus dem Klassendiagramm übernommen. Fehlende System-, Route- und
  Routenhaltmethoden sowie der zusätzliche Parameter der Restfahrzeitmethode sind im Code
  als gedankliche Ergänzungen vermerkt.
- Statische Strukturprüfung erfolgreich: ein `@startuml`/`@enduml`, fünf synchrone Aufrufe,
  fünf Antworten, fünf passende Aktivierungs-/Deaktivierungspaare, geschlossener Loop und
  ausgeglichene Klammern.
- Kompilierung und Rendering nicht geprüft: Java 17 ist vorhanden, aber lokal fehlen
  PlantUML-Kommando und PlantUML-JAR. `v1-plantuml.png` bleibt offen.
