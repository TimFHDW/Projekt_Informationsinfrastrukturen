# Evaluation: easyride / claude / klassendiagramm

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyride-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

> Quelle fuer K2/K3: `lastenhefte/easyride.md`.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 5 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Struktur-Vorpruefung: `@startuml/@enduml` paarig, alle `note`-Bloecke geschlossen, jede
  Assoziation mit Multiplizitaeten, `{ordered}` an der Route-Routenhalt-Komposition.
- Direktes Bild (`v1-direkt-easyride.png`, Nachtrag 2026-07-07) – UML-Notation korrekt?:
  ja (vorlaeufige Selbstbewertung): Klassen mit 3 Kompartimenten und Sichtbarkeiten (+/-),
  hohle Raute (Aggregation Flotte–Fahrzeug), gefuellte Raute (Komposition Route–Routenhalt),
  Multiplizitaeten an allen Assoziationen, `{ordered}`, Constraints/Regeln als Notizen.
  Einschraenkung: Bild nachtraeglich aus `v1.puml` abgeleitet (siehe notizen.md, Nachtrag).

## K2 – Inhaltliche Korrektheit — Score: 5 (vorlaeufig)

Abgleich mit `lastenhefte/easyride.md`, konkrete Befunde:

- Alle vom Prompt geforderten Klassen vorhanden: Haltepunkt, Verbindung, Fahrzeug, Route,
  Routenhalt, Fahrgast, Fahrer, Fahrt (+ Flotte, Tablet). ✓
- `Verbindung` verbindet genau zwei Haltepunkte (Multiplizitaet 2) und ist als ungerichtet
  gekennzeichnet. ✓
- Kapazitaetsregel (Fahrgaeste <= Sitzplaetze) und Zentrale-Regel (Start/Ende, kein
  Ein-/Ausstieg) als Constraints/Notizen abgebildet. ✓
- Reihenfolge der Halte ueber `{ordered}` an `Route *-- Routenhalt`. ✓
- Pro Halt aufzunehmende/abzusetzende Fahrgaeste ueber zwei Assoziationen `Routenhalt–Fahrgast`. ✓
- Geforderte Kernmethoden vorhanden (buchen, Wartezeit, Restfahrzeit, naechsten Haltepunkt,
  Ankunft bestaetigen). ✓
- Keine erfundenen Features. ✓

## K3 – Vollstaendigkeit — Score: 4 (vorlaeufig)

- Mindestanforderung (UC ≥ 5 / Aktivitaeten ≥ 5 / Aufrufe ≥ 5): n. a. (nur andere Diagrammtypen).
- Fehlende zentrale Elemente: keine. Bewusste Vereinfachungen (peripher): „Zentrale" als
  boolean-Attribut statt eigener Subklasse; keine Personen-Oberklasse fuer Fahrer/Fahrgast;
  `Fahrgast` und buchender Kunde in einer Klasse zusammengefasst; Tablet ohne eigene Operationen.
- Artefakt-Ebene (DoD): direktes Bild liegt vor (`v1-direkt-easyride.png`, 2026-07-07);
  PlantUML-Rendering liegt vor (2026-07-14).

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: 3, Befunde: gerendert; lesbar, aber sehr lange Auto-Layout-Boegen (an, besteht aus) ueber die ganze Breite und Kreuzungen um Fahrt/Fahrzeug/Haltepunkt.
- Direktes Bild — Score: 4 (vorlaeufig, Selbstbewertung 2026-07-07). Befunde: Layout ohne
  Ueberlappungen, Beschriftungen vollstaendig lesbar; Abzuege: lange Umgehungskante
  Fahrt–Fahrzeug („zugeteilt") ueber den unteren Bildrand und Label-Gedraenge am oberen Rand
  von `Fahrzeug` (drei Assoziationsenden dicht beieinander).

## PlantUML vs. direkt – Unterschiede

- Direktes Bild liegt vor (2026-07-07); PlantUML gerendert (2026-07-14), Layout-Vergleich
  daher noch nicht moeglich. Wichtig: Das direkte Bild wurde nachtraeglich aus `v1.puml`
  abgeleitet – inhaltliche Uebereinstimmung ist konstruktionsbedingt und kein unabhaengiger
  Befund; fuer `vergleiche/plantuml-vs-direkt.md` nur die Zeichenqualitaet (K4) heranziehen.

## Was haetten wir anders modelliert?

- „Zentrale" als eigene Subklasse von `Haltepunkt` statt boolean-Flag.
- Gemeinsame Oberklasse `Person` fuer `Fahrer` und `Fahrgast` (Name-Attribut).
- `Routenhalt` alternativ als echte Assoziationsklasse zwischen `Route` und `Haltepunkt`.
- Trennung von buchendem `Kunde` und transportiertem `Fahrgast`, falls fachlich noetig.

## Sonstige Beobachtungen

- Methodik-Abweichung: Generierung in laufender Cowork-Session, nicht in frischer, isolierter
  Chat-Session -> moeglicher Kontext-Einfluss; fuer belastbaren Vergleich reproduzieren.
- Zweistufiger Prompt nicht getrennt ausgefuehrt; Diagramm direkt erzeugt.
- Details siehe `notizen.md`.

## Hinweis 2026-07-14: abgeschnittenes Dateiende wiederhergestellt

- Die Arbeitskopie dieser Datei (und Commit e69849d) endete mitten im Satz ("...Assoziationsenden dic").
  Die fehlenden Abschnitte wurden am 2026-07-14 aus Commit 9ef275b wiederhergestellt; die
  heute ergaenzten K1-/K4-PlantUML-Befunde blieben erhalten. In den wiederhergestellten
  Abschnitten wurde die veraltete Angabe "PlantUML-Rendering weiterhin offen" auf
  "gerendert (2026-07-14)" aktualisiert (analog zur easylib-Fassung vor dem Abschnitt).
  Details und Begruendung: Journal (dokumentation/vorgehen.md), Eintrag vom 2026-07-14.

## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1) - Bewertung offen

- `v2.puml`, `v2-direkt.png` und `v2-plantuml.png` liegen vor (s. notizen.md, Nachtrag v2).
  Diese Datei bewertet weiterhin v1; die vollstaendige v2-Bewertung (K2-K4) steht aus.
- K1-Vorbefund v2: `v2.puml` kompiliert fehlerfrei - am 2026-07-14 in der Cowork-Sandbox
  gerendert (plantuml.jar 1.2019.06 aus dem npm-Paket node-plantuml); keine Korrektur
  noetig, kein `v2-korrigiert.puml`.
- Vorlaeufige Sichtpruefung v2 (kein Ersatz fuer die Bewertung): alle Schritt-2-Pflichtklassen vorhanden
  (inkl. eigener Klasse `Routenhalt` mit Begruendung), `{ordered}` an der
  Route-Routenhalt-Komposition, `Verbindung` ungerichtet mit Multiplizitaet 2,
  Kapazitaets- und Zentrale-Regel als Constraint-Notizen, Multiplizitaeten an allen
  Assoziationen, alle geforderten Kernmethoden.
