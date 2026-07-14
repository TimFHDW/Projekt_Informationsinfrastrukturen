# Notizen: easylib / chatgpt / sequenz

## Generierung v1

- Datum der Generierung: 2026-07-14
- KI: ChatGPT/Codex, Built-in Imagegen
- Prompt: `prompts/sequenz/easylib-v1.md`
- Szenario: „Bibliothekar verleiht ein Buchexemplar an einen Kunden“
- Originalartefakt: `v1-direkt.png`
- Bilddaten: 1693 × 929 px, 976.968 Bytes
- SHA-256: `CA977EED5CA90A92A41EA674DFEE209E982DD52D39766B0D4F1B33B7EC484971`
- Generierungsweg: eigenständiger Built-in-Imagegen-Aufruf ohne Referenzbild; das zuerst
  erzeugte PNG wurde unverändert aus dem Imagegen-Ausgabeordner in die DoD-Zelle kopiert.
- Methodikabweichung: Schritt 1 und Schritt 2 der Promptdatei wurden für das Bild in einer
  strukturierten Generierungsanweisung zusammengeführt; der vorgesehene Verständnis-Check
  zwischen zwei Nachrichten entfiel.
- PlantUML-Code und PlantUML-Rendering: in diesem Arbeitsschritt nicht erzeugt.
- Quellenhinweis: `lastenhefte/easylib.md` ist vorhanden und wurde nur gelesen; die
  gegenteilige Statusangabe in `lastenhefte/README.md` ist veraltet.

## Rohbeobachtungen zur Sichtprüfung

- Sechs synchrone Methodenaufrufe mit jeweils einem gestrichelten Antwortpfeil vorhanden.
- Bibliothekar ist als Akteur dargestellt; die fachlich geforderten Objekt-Lebenslinien sind
  enthalten.
- Kunde und Buchexemplar werden ID-basiert ermittelt; Verfügbarkeit, Ausleihe mit Leihfrist,
  Statusaktualisierung und Bestätigung sind vollständig.
- Werk-/Exemplartrennung ist durch die Lebenslinie `Buchexemplar` und eine Notiz eindeutig.
- `«create»` ist sichtbar, aber Teilnehmerkopf und Lebenslinie der `Ausleihe` beginnen
  fälschlich bereits oben statt erst an der Erzeugungsnachricht.
- Bild ist scharf, vollständig und ohne Überlappungen lesbar.

## Offene DoD-Punkte

- [ ] `v1.puml`
- [ ] `v1-plantuml.png` oder `.svg`
- [x] `v1-direkt.png`
- [x] `evaluation.md` (Direktbild vollständig, PlantUML-Anteile offen)
- [x] `notizen.md`
- [x] Journal-Eintrag
- [x] Ergebnismatrix auf `generiert` / v1 aktualisiert
