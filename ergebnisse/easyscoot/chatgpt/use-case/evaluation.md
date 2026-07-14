# Evaluation: easyscoot / chatgpt / use-case

| | |
|---|---|
| Bewertet von | Codex (Sichtprüfung) |
| Datum | 2026-07-14 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easyscoot-v1.md` |
| Rendering-Weg | nicht vorhanden – in diesem Arbeitsschritt wurde nur das Direktbild erzeugt |

Skalen und Regeln: `evaluation/kriterien.md`. PlantUML-Code und -Rendering fehlen; die
PlantUML-Anteile bleiben deshalb offen.

## K1 – Syntaktische Korrektheit — Score: offen (Direktbild: 3/5)

- PlantUML kompiliert ohne Korrektur: nicht prüfbar; `v1.puml` fehlt.
- Fehlerliste: PlantUML nicht vorhanden. Mehrere Assoziationslinien laufen auf gemeinsame
  Punkte neben den Akteursfiguren zu, ohne die Akteure sichtbar zu berühren. Rechts führen
  Linien an Akteuren vorbei oder enden an einem nicht als UML-Element definierten
  Linienknoten. Dadurch sind mehrere Assoziationen syntaktisch nicht eindeutig.
- Direktes Bild – UML-Notation korrekt?: Akteursfiguren, Systemgrenze und
  Use-Case-Ellipsen entsprechen grundsätzlich der UML-Notation. Die mehrfach fehlerhaften
  beziehungsweise mehrdeutigen Anschlüsse verhindern eine höhere Bewertung.

## K2 – Inhaltliche Korrektheit — Score: offen (Direktbild: 3/5)

Abgleich mit `lastenhefte/easyscoot.md`:

- Die Zuordnungen von Kunde, Flottenmanager und Service-Mitarbeiter zu ihren Funktionen
  entsprechen dem Lastenheft.
- Die externe E-Scooter-Software ist korrekt mit „Statusdaten übermitteln“ verbunden.
- Fehler: „Nutzung beenden“ ist im Bild mit der E-Scooter-Software verbunden. Fachlich muss
  hier das Rechnungssystem beteiligt sein, weil es den Preis für die Fahrtzusammenfassung
  berechnet.
- Fehler: „Wartungsmodus beenden“ ist sichtbar mit dem Rechnungssystem verbunden, obwohl
  beim Beenden der Wartung die E-Scooter-Software per Mobilfunk wieder angemeldet wird.
- Die Verbindung von „Wartungsmodus starten“ zur E-Scooter-Software endet in einer
  mehrdeutigen Linienstruktur und ist nicht verlässlich ablesbar.
- Keine erfundene Bezahlfunktion oder sonstige fachfremde Funktion festgestellt.

## K3 – Vollständigkeit — Score: offen (Direktbild: 3/5)

- Mindestanforderung erfüllt (Use Cases ≥ 5): ja; elf Use Cases sind dargestellt.
- Alle im Diagramm-Prompt beispielhaft aufgeführten Use Cases sowie die fachlich abgeleitete
  Statusübermittlung sind vorhanden.
- Zentrale Lücken: Die Beteiligung des Rechnungssystems an „Nutzung beenden“ sowie die
  Beteiligung der E-Scooter-Software an Start und Ende des Wartungsmodus sind wegen falscher
  oder mehrdeutiger Assoziationen nicht vollständig abgebildet.

## K4 – Lesbarkeit / Zeichenqualität

- PlantUML-Rendering — Score: offen, Befunde: `v1-plantuml.png` bzw. `.svg` fehlt.
- Direktes Bild — Score: 3/5, Befunde: Text und einzelne Elemente sind scharf und gut
  lesbar. Die dichten Linienfächer links und insbesondere die langen, teils mehrdeutigen
  Linienführungen rechts erschweren jedoch die Zuordnung.

## PlantUML vs. direkt – Unterschiede

- Nicht bewertbar, da PlantUML-Code und -Rendering noch nicht vorliegen.

## Was hätten wir anders modelliert?

- Das Rechnungssystem ausschließlich mit „Nutzung beenden“ verbinden.
- Die E-Scooter-Software eindeutig mit „Statusdaten übermitteln“, „Wartungsmodus starten“
  und „Wartungsmodus beenden“ verbinden und jede Linie direkt am Akteur enden lassen.
- Die Akteure und Use Cases so gruppieren, dass kürzere Einzellinien ohne Sammelpunkte
  entstehen.

## Sonstige Beobachtungen

- Das Bild wurde in einem eigenständigen Built-in-Imagegen-Durchlauf erzeugt und
  unverändert als `v1-direkt.png` abgelegt.
- Die zwei Prompt-Schritte wurden für die Bildgenerierung zu einer strukturierten
  Spezifikation zusammengeführt; ein separater Verständnis-Check fand nicht statt.

