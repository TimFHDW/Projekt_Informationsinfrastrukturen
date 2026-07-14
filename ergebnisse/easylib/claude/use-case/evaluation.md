# Evaluation: easylib / claude / use-case

| | |
|---|---|
| Bewertet von | Alex (mit Claude/Cowork); Direktbild-Abschnitte: Claude-Selbstbewertung (vorlaeufig) |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easylib-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 5 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Fehlerliste (aus `notizen.md` / `vN-korrigiert.puml`): Sichtpruefung ohne Befund;
  verbindliche Bewertung erst nach Rendering
- Direktes Bild (`v1-direkt-easylib.png`, Nachtrag 2026-07-07) – UML-Notation korrekt?:
  ja (vorlaeufige Selbstbewertung): Akteure als Strichmaennchen ausserhalb der benannten
  Systemgrenze "EasyLib", Sekundaerakteure mit Stereotyp «externes System», Use Cases als
  Ellipsen, ungerichtete Assoziationen, extend als gestrichelter offener Pfeil mit
  «extend»-Label in Richtung Basis-Use-Case "Exemplar einpflegen". Einschraenkung: Bild
  nachtraeglich aus `v1.puml` abgeleitet (s. notizen.md, Nachtrag).

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
- Artefakt-Ebene (DoD): direktes Bild liegt vor (`v1-direkt-easylib.png`, 2026-07-07);
  PlantUML-Rendering liegt vor (2026-07-14).

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: 4, Befunde: gerendert; Akteure links, Use Cases mittig, externe Systeme rechts; wenige Kreuzungen.
- Direktes Bild — Score: 4/5 (vorlaeufig, Selbstbewertung 2026-07-07). Befunde: alle 15
  Ellipsen ueberlappungsfrei, extend-Pfeil samt «extend»-Label erkennbar, Beschriftungen
  lesbar; Abzuege: mehrere Kreuzungen zwischen Bibliothekar- und Kunde-Kanten (geteilte
  Use Cases "Bestand durchsuchen" / "Standort und Status") und sehr kurzer extend-Pfeil
  zwischen den eng stehenden Ellipsen UC1/UC2.

## PlantUML vs. direkt – Unterschiede

- Direktes Bild liegt vor (2026-07-07); PlantUML gerendert (2026-07-14), ein
  Layout-Vergleich ist daher noch nicht moeglich. Wichtig: Das direkte Bild wurde
  nachtraeglich aus `v1.puml` abgeleitet – inhaltliche Uebereinstimmung ist
  konstruktionsbedingt und kein unabhaengiger Befund; fuer
  `vergleiche/plantuml-vs-direkt.md` nur die Zeichenqualitaet (K4) heranziehen.

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
