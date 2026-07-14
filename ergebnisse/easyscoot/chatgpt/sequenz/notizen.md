# Notizen: easyscoot / chatgpt / sequenz

## Generierung v1

- Datum der Generierung: 2026-07-14
- KI: ChatGPT/Codex, Built-in Imagegen
- Prompt: `prompts/sequenz/easyscoot-v1.md`
- Szenario: „Kunde beendet die Nutzung eines E-Scooters“
- Originalartefakt: `v1-direkt.png`
- Bilddaten: 1693 × 929 px, 967.260 Bytes
- SHA-256: `230703BFAE2A33A2DE9DAF0A66A5540BF4F8EC5B23CBD17C1F2BA309C66F9016`
- Generierungsweg: eigenständiger Built-in-Imagegen-Aufruf ohne Referenzbild; das zuerst
  erzeugte PNG wurde unverändert aus dem Imagegen-Ausgabeordner in die DoD-Zelle kopiert.
- Methodikabweichung: Schritt 1 und Schritt 2 der Promptdatei wurden für das Bild in einer
  strukturierten Generierungsanweisung zusammengeführt; der vorgesehene Verständnis-Check
  zwischen zwei Nachrichten entfiel.
- PlantUML-Code und PlantUML-Rendering: in diesem Arbeitsschritt nicht erzeugt.

## Rohbeobachtungen zur Sichtprüfung

- Fünf synchrone Methodenaufrufe und die fünf geforderten Lebenslinien vorhanden.
- Kunde ist als Akteur, Rechnungssystem als externes System und die übrigen Beteiligten als
  Objekt-Lebenslinien dargestellt.
- Preis wird ausschließlich durch das Rechnungssystem berechnet; Dauer, Kilometer und
  Wattstunden werden als Parameter übergeben.
- Fehler: Eine erste `Fahrtzusammenfassung` geht vor Ermittlung der Fahrtdaten und des
  Preises an den Kunden; am Ende folgt die fachlich richtige zweite Rückgabe.
- Bild ist scharf, vollständig und ohne Überlappungen lesbar.

## Offene DoD-Punkte

- [ ] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] `v1-direkt.png`
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert
