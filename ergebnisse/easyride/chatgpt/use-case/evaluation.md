# Evaluation: easyride / chatgpt / use-case

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easyride-v1.md` |
| Rendering-Weg | nicht vorhanden – in diesem Arbeitsschritt wurde nur das Direktbild erzeugt |

Skalen und Regeln: `evaluation/kriterien.md`. PlantUML-Code und -Rendering fehlen; die
PlantUML-Anteile bleiben deshalb offen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 4/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML nicht vorhanden. Im Direktbild enden die Assoziationslinien jeweils
  mit einem kleinen sichtbaren Abstand vor den Akteursfiguren, statt diese eindeutig zu
  berühren. Der Mangel ist lokal und ändert die erkennbare Zuordnung nicht.
- Direktes Bild – UML-Notation korrekt?: Systemgrenze, zwei Akteure, fünf
  Use-Case-Ellipsen und einfache Assoziationen sind korrekt gewählt; abgesehen von den
  kleinen Anschlusslücken wurde kein weiterer Notationsfehler festgestellt.

## K2 – Inhaltliche Korrektheit — Score: offen (Direktbild: 5/5)

Abgleich mit `lastenhefte/easyride.md`:

- Der Akteur Kunde (Fahrgast) ist mit „Fahrt buchen“, „Wartezeit abfragen (vor
  Fahrtantritt)“ und „Restfahrzeit abfragen (nach Fahrtantritt)“ verbunden.
- Der Akteur Fahrer ist mit „Nächsten Haltepunkt mit Fahrgastwechsel abfragen“ und
  „Erreichen eines Haltepunkts bestätigen“ verbunden.
- Damit entsprechen Akteure, Leistungen und Zuordnungen vollständig den beiden
  abschließenden Leistungslisten des Lastenhefts; erfundene Funktionen wurden nicht
  festgestellt.

## K3 – Vollständigkeit — Score: offen (Direktbild: 5/5)

- Mindestanforderung erfüllt (Use Cases ≥ 5): ja; genau fünf Use Cases sind dargestellt.
- Fehlende zentrale Elemente: keine für ein Use-Case-Diagramm auf Basis der im Lastenheft
  abschließend genannten Leistungen.
- Die im Prompt nur zur Diskussion gestellte interne Routenplanung wurde folgerichtig nicht
  als zusätzlicher, akteursbezogener Use Case aufgenommen.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 5/5, Befunde: klare Links-rechts-Gruppierung nach Akteur,
  kontrastreiche und scharfe Beschriftungen, keine Kreuzungen, Überlappungen oder
  abgeschnittenen Elemente.

## PlantUML vs. direkt – Unterschiede

- Nicht bewertbar, da PlantUML-Code und -Rendering noch nicht vorliegen.

## Was hätten wir anders modelliert?

- Die fünf Assoziationslinien direkt bis an die Akteursfiguren führen. Inhaltlich ist keine
  abweichende Modellierung erforderlich.

## Sonstige Beobachtungen

- Das Bild wurde in einem eigenständigen Built-in-Imagegen-Durchlauf erzeugt und
  unverändert als `v1-direkt.png` abgelegt.
- Die zwei Prompt-Schritte wurden für die Bildgenerierung zu einer strukturierten
  Spezifikation zusammengeführt; ein separater Verständnis-Check fand nicht statt.

