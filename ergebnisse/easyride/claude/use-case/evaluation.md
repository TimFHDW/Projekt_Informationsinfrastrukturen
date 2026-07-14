# Evaluation: easyride / claude / use-case

| | |
|---|---|
| Bewertet von | Alex (mit Claude/Cowork); Direktbild-Abschnitte: Claude-Selbstbewertung (vorlaeufig) |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/use-case/easyride-v1.md` |
| Rendering-Weg | noch offen (jar-Download blockiert, s. notizen.md) |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: _/5 (offen)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft (kein Renderer verfuegbar)
- Fehlerliste (aus `notizen.md` / `vN-korrigiert.puml`): Sichtpruefung ohne Befund;
  verbindliche Bewertung erst nach Rendering
- Direktes Bild (`v1-direkt-easyride.png`, Nachtrag 2026-07-07) – UML-Notation korrekt?:
  ja (vorlaeufige Selbstbewertung): Akteure als Strichmaennchen ausserhalb der benannten
  Systemgrenze "EasyRide", Use Cases als Ellipsen, ungerichtete Assoziationen; keine
  include/extend (wie im Modell). Einschraenkung: Bild nachtraeglich aus `v1.puml`
  abgeleitet (s. notizen.md, Nachtrag).

## K2 – Inhaltliche Korrektheit — Score: 5/5 (vorlaeufig)

Abgleich mit `lastenhefte/easyride.md`, konkrete Befunde:

- Alle 5 Use Cases entsprechen exakt den beiden Leistungslisten des Lastenhefts;
  keine erfundenen Features (keine Bezahlung, Bewertung, kein GPS-Tracking).
- Akteure Kunde (Fahrgast) und Fahrer korrekt; keine erfundenen Akteure
  (Zentrale/Disponent kommt im Lastenheft nicht als handelnde Person vor).
- Verzicht auf include/extend fachlich sauber begruendet.
- Diskussionswuerdig (kein Fehler): Routenplanung fehlt bewusst als Use Case –
  im Lastenheft ist sie Systemreaktion auf die Buchung, kein Akteurs-Ziel.
- Vorlaeufig: unabhaengige Zweitpruefung durch Menschen steht aus.

## K3 – Vollstaendigkeit — Score: 5/5 (vorlaeufig)

- Mindestanforderung erfuellt (UC >= 5): ja, genau 5 Use Cases
- Fehlende zentrale Elemente: keine gefunden. Beide Leistungslisten sind
  vollstaendig abgebildet; das Lastenheft nennt keine weiteren Nutzerleistungen.
- Artefakt-Ebene (DoD): direktes Bild liegt vor (`v1-direkt-easyride.png`, 2026-07-07);
  PlantUML-Rendering steht weiterhin aus.

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: _/5 (offen), Befunde: Rendering steht aus
- Direktes Bild — Score: 5/5 (vorlaeufig, Selbstbewertung 2026-07-07). Befunde: klares
  Spaltenlayout, keine Kanten- oder Elementueberlappungen, alle Beschriftungen frei und
  lesbar; mit 5 Use Cases und 2 Akteuren das einfachste der drei Use-Case-Diagramme.

## PlantUML vs. direkt – Unterschiede

- Direktes Bild liegt vor (2026-07-07); PlantUML-Rendering weiterhin offen, ein
  Layout-Vergleich ist daher noch nicht moeglich. Wichtig: Das direkte Bild wurde
  nachtraeglich aus `v1.puml` abgeleitet – inhaltliche Uebereinstimmung ist
  konstruktionsbedingt und kein unabhaengiger Befund; fuer
  `vergleiche/plantuml-vs-direkt.md` nur die Zeichenqualitaet (K4) heranziehen.

## Was haetten wir anders modelliert?

- Ob "Naechsten Haltepunkt mit Fahrgastwechsel abfragen" in zwei Use Cases
  (Haltepunkt / Fahrgastnamen) zu trennen waere – Lastenheft nennt es in einem
  Punkt, daher hier ein Use Case.
- Alternativ liesse sich die Zentrale als Sekundaerakteur der Routenplanung
  diskutieren; das Lastenheft gibt dafuer aber keinen menschlichen oder externen
  Akteur her – daher verworfen.

## Sonstige Beobachtungen

- Generierung in laufender Session mit Vorkontext (easylib-Use-Case-Zelle) –
  moeglicher context bleed, s. notizen.md.
- Mit genau 5 Use Cases liegt das Diagramm exakt an der Mindestgrenze; das ist
  durch die abschliessenden Leistungslisten des Lastenhefts gedeckt, nicht durch
  Sparsamkeit der KI.
