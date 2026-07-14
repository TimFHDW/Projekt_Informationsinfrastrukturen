# Evaluation: easylib / chatgpt / use-case

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easylib-v1.md` |
| Rendering-Weg | nicht vorhanden – in diesem Arbeitsschritt wurde nur das Direktbild erzeugt |

Skalen und Regeln: `evaluation/kriterien.md`. PlantUML-Code und -Rendering fehlen; die
PlantUML-Anteile bleiben deshalb offen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 3/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML nicht vorhanden. Mehrere Assoziationslinien laufen auf gemeinsame
  Punkte neben den Akteursfiguren zu, ohne die Akteure sichtbar zu berühren. Die beiden
  Paare gleichnamiger Use Cases sind jeweils durch eine unbeschriftete Volllinie verbunden;
  eine solche Use-Case-zu-Use-Case-Beziehung ist keine gültige UML-Semantik. Im unteren
  Bereich verbindet eine weitere mehrdeutige Linienführung fachlich unabhängige Use Cases.
- Direktes Bild – UML-Notation korrekt?: Systemgrenze, Akteursfiguren und Ellipsen sind
  grundsätzlich korrekt. Die gestrichelte `<<extend>>`-Beziehung zeigt fachlich richtig vom
  optionalen Import auf „Exemplar einpflegen“. Die mehrfachen ungültigen oder
  mehrdeutigen Volllinien verhindern eine höhere Bewertung.

## K2 – Inhaltliche Korrektheit — Score: offen (Direktbild: 3/5)

Abgleich mit `lastenhefte/easylib.md`:

- Die geforderten Rollen, externen Systeme und Funktionsbezeichnungen sind vorhanden.
- Der optionale Import der Buchdaten ist fachlich plausibel als `<<extend>>` von „Exemplar
  einpflegen“ modelliert; der Verbundkatalog ist mit dem Import verbunden.
- Fehler: „Bestand durchsuchen“ wurde zweimal gezeichnet, statt als ein gemeinsamer Use Case
  von Bibliothekar und Kunde verwendet zu werden.
- Fehler: „Standort und Status einsehen“ wurde ebenfalls zweimal gezeichnet, obwohl beide
  Rollen dieselbe Systemfunktion nutzen.
- Fehler: Die vernetzten Bibliotheken sind sichtbar mit „Leihfrist verlängern“ verbunden;
  fachlich müssen sie am Use Case „Bestand vernetzter Bibliotheken durchsuchen“ beteiligt
  sein.
- Fehler: „Kundendaten einsehen“ besitzt keine erkennbare Assoziation zum Bibliothekar.
- Keine E-Books, Gebührenzahlung, Empfehlungen oder sonstige fachfremde Funktionen
  festgestellt.

## K3 – Vollständigkeit — Score: offen (Direktbild: 3/5)

- Mindestanforderung erfüllt (Use Cases ≥ 5): ja; dargestellt sind 17 Ellipsen.
- Alle im Diagramm-Prompt aufgeführten Funktionsbezeichnungen sowie „Standort und Status
  einsehen“ und der Katalogimport sind vorhanden.
- Zentrale Lücken beziehungsweise Strukturfehler: Zwei gemeinsame Use Cases sind dupliziert,
  die Verbindung zu den vernetzten Bibliotheken ist falsch und die Bibliothekar-Zuordnung
  für „Kundendaten einsehen“ fehlt.
- Die geforderten genau 15 unterschiedlichen Use Cases wurden wegen der beiden Duplikate
  nicht eingehalten.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 3/5, Befunde: Beschriftungen und Einzelelemente sind scharf,
  kontrastreich und nicht abgeschnitten. Die dichten Linienfächer, duplizierten Ellipsen und
  die lange mehrdeutige Verbindung im unteren Bereich machen die Zuordnung unübersichtlich.

## PlantUML vs. direkt – Unterschiede

- Nicht bewertbar, da PlantUML-Code und -Rendering noch nicht vorliegen.

## Was hätten wir anders modelliert?

- Je nur eine Ellipse für „Bestand durchsuchen“ und „Standort und Status einsehen“ verwenden
  und beide Ellipsen jeweils direkt mit Bibliothekar und Kunde verbinden.
- Die vernetzten Bibliotheken ausschließlich mit „Bestand vernetzter Bibliotheken
  durchsuchen“ und den Bibliothekar direkt mit „Kundendaten einsehen“ verbinden.
- Die fachlich passende `<<extend>>`-Beziehung für den optionalen Import beibehalten.

## Sonstige Beobachtungen

- Das Bild wurde in einem eigenständigen Built-in-Imagegen-Durchlauf erzeugt und
  unverändert als `v1-direkt.png` abgelegt.
- Die zwei Prompt-Schritte wurden für die Bildgenerierung zu einer strukturierten
  Spezifikation zusammengeführt; ein separater Verständnis-Check fand nicht statt.
- Die Mehrdeutigkeit der Leihfristverlängerung ist im Use-Case-Diagramm nicht als
  Bedingungslogik dargestellt; sie wird dadurch weder aufgelöst noch zusätzlich verfälscht.

