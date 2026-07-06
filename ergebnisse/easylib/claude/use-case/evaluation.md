# Evaluation: easylib / claude / use-case

| | |
|---|---|
| Bewertet von | Alex (mit Claude/Cowork) |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easylib-v1.md` |
| Rendering-Weg | noch offen (jar-Download blockiert, s. notizen.md) |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: _/5 (offen)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft (kein Renderer verfuegbar)
- Fehlerliste (aus `notizen.md` / `vN-korrigiert.puml`): Sichtpruefung ohne Befund;
  verbindliche Bewertung erst nach Rendering
- Direktes Bild – UML-Notation korrekt?: n. a., v1-direkt.png liegt nicht vor

## K2 – Inhaltliche Korrektheit — Score: 5/5 (vorlaeufig)

Abgleich mit `lastenhefte/easylib.md`, konkrete Befunde:

- Alle 15 Use Cases sind durch das Lastenheft gedeckt; keine erfundenen Features
  (keine E-Book-Ausleihe, keine Gebuehren, kein Empfehlungssystem).
- Akteurszuordnung entspricht den drei Nutzergruppen; Verbundkatalog und vernetzte
  Bibliotheken korrekt als externe Sekundaerakteure.
- extend statt include fuer den Katalogimport ist durch "wahlweise ... statt manuell"
  gedeckt und begruendet.
- Diskussionswuerdig (kein Fehler): "Standort und Status einsehen" als eigener Use Case
  statt Teil von "Bestand durchsuchen" – Lastenheft fuehrt beides als getrennte Punkte.
- Vorlaeufig: unabhaengige Zweitpruefung durch Menschen steht aus.

## K3 – Vollstaendigkeit — Score: 5/5 (vorlaeufig)

- Mindestanforderung erfuellt (UC >= 5): ja, 15 Use Cases
- Fehlende zentrale Elemente: keine gefunden. Alle Aufzaehlungspunkte der drei
  Nutzergruppen sind abgebildet; "Mahnbescheide ausstellen" bewusst nicht als
  Use Case (Systemleistung ist nur die Uebersicht, s. notizen.md).

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: _/5 (offen), Befunde: Rendering steht aus
- Direktes Bild — Score: _/5 (offen), Befunde: liegt nicht vor

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar: direkte Bildform fehlt (s. notizen.md).

## Was haetten wir anders modelliert?

- Evtl. "Standort und Status einsehen" per <<include>> an "Bestand durchsuchen"
  koppeln oder zusammenfassen – haengt von der Lesart des Lastenhefts ab.
- Pruefenswert, ob "Exemplar verleihen" und "Rueckgabe entgegennehmen" den Kunden
  als beteiligten Sekundaerakteur erhalten sollten (er ist physisch beteiligt,
  bedient aber nicht das System) – hier bewusst weggelassen.

## Sonstige Beobachtungen

- Generierung in laufender Session mit Vorkontext (Lastenheft, aktivitaet-Zelle) –
  moeglicher context bleed, s. notizen.md.
- Prompt-Formulierung "Buch reservieren" uebernommen; konsistent mit der
  Werk-vs.-Exemplar-Regel (reserviert wird auf Werk-Ebene).
