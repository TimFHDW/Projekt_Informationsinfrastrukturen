# Evaluation: easyride / chatgpt / sequenz

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easyride-v1.md` |
| Rendering-Weg | Direktbild: Built-in Imagegen; PlantUML-Rendering offen |

Skalen und Regeln: `evaluation/kriterien.md`. In dieser Zelle liegt bislang nur das
Direktbild vor; PlantUML-Code und -Rendering bleiben offen und werden nicht bewertet.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 5/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: für PlantUML offen.
- Direktes Bild – UML-Notation korrekt?: ja. Akteur, Objekt-Lebenslinien,
  Aktivierungsbalken, durchgezogene synchrone Aufrufe und gestrichelte Antwortpfeile sind
  eindeutig und konsistent notiert. Jeder der fünf Aufrufe besitzt eine Antwort.

## K2 – Inhaltliche Korrektheit — Score: offen (Direktbild: 4/5)

Abgleich mit `lastenhefte/easyride.md`:

- Der Fahrer bestätigt über sein Tablet die Ankunft; das System aktualisiert den
  Routenfortschritt und die verbleibende Fahrzeit und liefert anschließend den nächsten
  Haltepunkt samt Namen der aufzunehmenden und abzusetzenden Fahrgäste zurück.
- Die Aktualisierung der verbleibenden Fahrzeit hängt wie gefordert vom zuletzt erreichten
  Haltepunkt ab. Es wurden keine Bezahl-, Bewertungs- oder sonstigen fachfremden Funktionen
  ergänzt; die Regeln zu Kapazität und Zentrale werden nicht verletzt.
- Kleinere Ungenauigkeit: `ermittleFahrgastwechsel(haltepunktId)` steht vor
  `ermittleNächstenHaltepunkt()` und wirkt damit auf den gerade bestätigten statt eindeutig
  auf den nächsten Haltepunkt bezogen. Die zusätzliche Lebenslinie `Betroffene Fahrgäste`
  bleibt ungenutzt; die zugehörige Aktualisierung erfolgt ausschließlich an
  `Buchung/Fahrt`.

## K3 – Vollständigkeit — Score: offen (Direktbild: 5/5)

- Mindestanforderung erfüllt (Aufrufe ≥ 5): ja; fünf synchrone Methodenaufrufe und fünf
  Antwortpfeile sind vorhanden.
- Alle geforderten fachlichen Stationen sind abgebildet: Ankunft bestätigen,
  Routenfortschritt aktualisieren, Fahrgastwechsel ermitteln, verbleibende Fahrzeit der
  betroffenen Fahrten aktualisieren und nächsten Haltepunkt mit Fahrgastnamen zurückgeben.
- Fehlende zentrale Elemente im Direktbild: keine. Die ungenutzte zusätzliche Lebenslinie
  ist eine Modellierungsunschärfe, keine fachliche Lücke.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: scharfes Querformat, große Beschriftungen, klare
  zeitliche Leserichtung, keine Überlappungen und keine abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar, da PlantUML-Code und -Rendering fehlen.

## Was hätten wir anders modelliert?

- Die Lebenslinie `Betroffene Fahrgäste` weglassen oder aktiv in die Aktualisierung
  einbeziehen. Außerdem zuerst den nächsten Haltepunkt bestimmen und danach dessen
  aufzunehmende und abzusetzende Fahrgäste ermitteln.

## Sonstige Beobachtungen

- Das Bild wurde als eigenständige, direkte Bildgenerierung ohne PlantUML- oder
  Bildreferenz erzeugt und unverändert gespeichert.
- Die zwei Prompt-Schritte wurden technisch zu einer strukturierten Bildspezifikation
  zusammengeführt; ein separater Verständnis-Check fand nicht statt.
