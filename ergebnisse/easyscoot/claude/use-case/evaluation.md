# Evaluation: easyscoot / claude / use-case

| | |
|---|---|
| Bewertet von | Alex (mit Claude/Cowork) |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easyscoot-v1.md` |
| Rendering-Weg | noch offen (jar-Download blockiert, s. notizen.md) |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: _/5 (offen)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft (kein Renderer verfuegbar)
- Fehlerliste (aus `notizen.md` / `vN-korrigiert.puml`): Sichtpruefung ohne Befund;
  verbindliche Bewertung erst nach Rendering
- Direktes Bild – UML-Notation korrekt?: n. a., v1-direkt.png liegt nicht vor

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

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: _/5 (offen), Befunde: Rendering steht aus
- Direktes Bild — Score: _/5 (offen), Befunde: liegt nicht vor

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar: direkte Bildform fehlt (s. notizen.md).

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
