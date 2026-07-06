# Evaluation: easyride / claude / klassendiagramm

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyride-v1.md` |
| Rendering-Weg | ausstehend – in dieser Session kein PlantUML-Rendering moeglich |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

> Quelle fuer K2/K3: `lastenhefte/easyride.md`.

## K1 – Syntaktische Korrektheit — Score: offen (Rendering ausstehend)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft – kein Renderlauf moeglich.
  Im Team-Renderweg pruefen und Ergebnis hier eintragen.
- Struktur-Vorpruefung: `@startuml/@enduml` paarig, alle `note`-Bloecke geschlossen, jede
  Assoziation mit Multiplizitaeten, `{ordered}` an der Route-Routenhalt-Komposition.
- Direktes Bild – UML-Notation korrekt?: n. v. – keine „direkt"-Bildform erzeugt.

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
- Artefakt-Ebene (DoD): „direkt"-Bildform fehlt; Rendering steht aus.

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: offen, Befunde: noch nicht gerendert (viele Assoziationen an
  `Haltepunkt`/`Fahrgast` – Kreuzungsgefahr, erst nach Rendering beurteilbar).
- Direktes Bild — Score: n. v.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden, kein direktes Bild, kein Rendering.

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
