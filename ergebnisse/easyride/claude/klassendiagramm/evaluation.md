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
  von `Fahrzeug` (drei Assoziationsenden dic