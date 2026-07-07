# Evaluation: easyscoot / claude / use-case

| | |
|---|---|
| Bewertet von | Alex (mit Claude/Cowork); Direktbild-Abschnitte: Claude-Selbstbewertung (vorlaeufig) |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easyscoot-v1.md` |
| Rendering-Weg | noch offen (jar-Download blockiert, s. notizen.md) |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: _/5 (offen)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft (kein Renderer verfuegbar)
- Fehlerliste (aus `notizen.md` / `vN-korrigiert.puml`): Sichtpruefung ohne Befund;
  verbindliche Bewertung erst nach Rendering
- Direktes Bild (`v1-direkt-easyscoot.png`, Nachtrag 2026-07-07) – UML-Notation korrekt?:
  ja (vorlaeufige Selbstbewertung): Akteure als Strichmaennchen ausserhalb der benannten
  Systemgrenze "EasyScoot", Sekundaerakteure mit Stereotyp «externes System», Use Cases
  als Ellipsen, ungerichtete Assoziationen; keine include/extend (wie im Modell).
  Einschraenkung: Bild nachtraeglich aus `v1.puml` abgeleitet (s. notizen.md, Nachtrag).

## K2 – Inhaltliche Korrektheit — Score: 5/5 (vorlaeufig)

Abgleich mit `lastenhefte/easyscoot.md`, konkrete Befunde:

- Alle 11 Use Cases sind durch das Lastenheft gedeckt; keine erfundenen Features
  (keine Bezahlfunktion, kein Bewertungssystem, kein Social Login).
- Akteurszuordnung korrekt: Kunde (4 UC), Flottenmanager (1 UC),
  Service-Mitarbeiter (6 UC); E-Scooter und Rechnungssystem als externe
  Sekundaerakteure an den fachlich richtigen Stellen.
- "Liste aller E-Scooter einsehen" korrekt als gemeinsamer Use Case beider
  Verwaltungsrollen.
- Diskussionswuerdig (kein Fehler): "Statusdaten uebermitteln" mit externem System
  als initiierendem Akteur ist UML-konform, aber eine Interpretationsentscheidung;
  ebenso "buchen und freischalten" als ein statt zwei Use Cases.
- Vorlaeufig: unabhaengige Zweitpruefung durch Menschen steht aus.

## K3 – Vollstaendigkeit — Score: 5/5 (vorlaeufig)

- Mindestanforderung erfuellt (UC >= 5): ja, 11 Use Cases
- Fehlende zentrale Elemente: keine gefunden. Alle im Prompt genannten Use Cases
  vorhanden; zusaetzlich die im Lastenheft geforderte Statusmeldung der Scooter.
  Die Fahrtzusammenfassung ist Teil von "Nutzung beenden" (Systemreaktion, kein
  eigener Use Case).
- Artefakt-Ebene (DoD): direktes Bild liegt vor (`v1-direkt-easyscoot.png`, 2026-07-07);
  PlantUML-Rendering steht weiterhin aus.

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: _/5 (offen), Befunde: Rendering steht aus
- Direktes Bild — Score: 4/5 (vorlaeufig, Selbstbewertung 2026-07-07). Befunde: alle 11
  Ellipsen und 5 Akteure ueberlappungsfrei, Beschriftungen lesbar; Abzuege: die Kante
  Rechnungssystem–"Nutzung beenden" kreuzt die E-Scooter-Kanten rechts der Systemgrenze,
  und die langen Faecherkanten von Service-Mitarbeiter und E-Scooter wirken unruhig.

## PlantUML vs. direkt – Unterschiede

- Direktes Bild liegt vor (2026-07-07); PlantUML-Rendering weiterhin offen, ein
  Layout-Vergleich ist daher noch nicht moeglich. Wichtig: Das direkte Bild wurde
  nachtraeglich aus `v1.puml` abgeleitet – inhaltliche Uebereinstimmung ist
  konstruktionsbedingt und kein unabhaengiger Befund; fuer
  `vergleiche/plantuml-vs-direkt.md` nur die Zeichenqualitaet (K4) heranziehen.

## Was haetten wir anders modelliert?

- "Gefilterte Liste einsehen" liesse sich alternativ als <<extend>> oder
  Spezialisierung von "Liste aller E-Scooter einsehen" modellieren; hier bewusst
  getrennt gelassen (eigene Leistung im Lastenheft, Prompt raet im Zweifel ab).
- "E-Scooter buchen und freischalten" koennte in zwei Use Cases getrennt werden,
  falls Buchung und Freischaltung zeitlich auseinanderfallen sollen; das Lastenheft
  beschreibt beides am Standort in einem Zug.

## Sonstige Beobachtungen

- Generierung in laufender Session mit Vorkontext (easylib- und easyride-Zellen) –
  moeglicher context bleed, s. notizen.md.
- Von den drei Systemen hat EasyScoot die meisten Akteure (5) und Use Cases (11);
  fuer den System-vs.-System-Vergleich interessant.
