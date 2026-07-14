# Evaluation: easylib / claude / klassendiagramm

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easylib-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

> Quelle fuer K2/K3: `lastenhefte/easylib.md` (offiziell, transkribiert aus OOSE-I Kapitel 4,
> Folien 180–183). Das Diagramm wurde am 2026-07-06 gegen dieses Lastenheft nachgeprueft –
> ohne noetige inhaltliche Aenderung am `v1.puml` (Original bleibt unveraendert, Regel 7).

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 5 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
  (z. B. plantuml.jar / IntelliJ-Plugin / plantuml.com) und Ergebnis hier eintragen.
- Struktur-Vorpruefung (nicht renderfrei-bestaetigend): `@startuml/@enduml` paarig, alle
  `note`-Bloecke paarig geschlossen, 11 Typen (1 Enum, 1 abstrakte + 8 Klassen + 2 externe
  Systeme), Enum `Genre` mit 9 Werten. Endgueltige K1-Bewertung erst nach Rendering.
- Direktes Bild (`v1-direkt-easylib.png`, Nachtrag 2026-07-07) – UML-Notation korrekt?:
  ja (vorlaeufige Selbstbewertung): abstrakte Klasse `Medium` kursiv, Vererbung mit hohlem
  Dreieck, Komposition Medium–Exemplar mit gefuellter Raute, `«enumeration»` Genre mit 9
  Werten, `«external system»`-Stereotypen, gestrichelte Abhaengigkeiten mit offener
  Pfeilspitze, Multiplizitaeten an allen Assoziationen (Autor 1..*), `{unique}`/`[0..1]`
  an Attributen. Einschraenkung: Bild nachtraeglich aus `v1.puml` abgeleitet (siehe
  notizen.md, Nachtrag).

## K2 – Inhaltliche Korrektheit — Score: 4 (vorlaeufig)

Abgleich mit `lastenhefte/easylib.md`, konkrete Befunde:

- Vererbung korrekt: gemeinsame bibliografische Merkmale (Titel, Verlag, Auflage,
  Erscheinungsdatum, ISBN, Genre, Autoren) nur in abstrakter Oberklasse `Medium`; `Buch`
  (seitenzahl) bzw. `Hoerbuch` (anzahlDatentraeger, spiellaengeMinuten) ergaenzen spezifisch. ✓
- Werk/Exemplar sauber getrennt: `Exemplar` mit id + Standort (etage, regalnummer),
  Komposition `Medium "1" *-- "1..*" Exemplar`. ✓
- `Autor` eigene Klasse, Multiplizitaet 1..* zum Medium; Mittelname/Namenszusatz optional. ✓
- `Genre` als Enumeration mit exakt den 9 vorgegebenen Werten. ✓
- Kunde (Name, Anschrift, Kunden-ID, Lichtbild), Ausleihe (mit Leihfrist), Reservierung,
  Verbundkatalog- und Vernetzte-Bibliothek-Schnittstelle vollstaendig gemaess Lastenheft. ✓
- Keine erfundenen Features. ✓
- Dokumentierte Abweichung (bewusst, per Prompt gefordert): Das Lastenheft sagt woertlich
  „eine Leihfrist zu verlaengern, soweit eine andere Reservierung vorliegt". Das Modell nimmt
  die fachlich plausiblere Gegenrichtung an (Verlaengern nur, wenn KEINE andere Reservierung
  vorliegt) und haelt dies als Notiz fest. → Bewusste, begruendete Abweichung, kein Fehler.
- Kleinere Ungenauigkeit: Ausleihe haengt am `Exemplar`, Reservierung am `Medium` (verallgemeinert
  auf Buch UND Hoerbuch), waehrend das Lastenheft Ausleihe/Reservierung sprachlich um
  „Buchexemplar"/„ein Buch" formuliert. Fachlich vertretbare Verallgemeinerung, aber ueber den
  woertlichen Text hinaus – deshalb Abzug auf 4.

## K3 – Vollstaendigkeit — Score: 4 (vorlaeufig)

- Mindestanforderung erfuellt (UC ≥ 5 / Aktivitaeten ≥ 5 / Aufrufe ≥ 5): n. a.
  (gilt nur fuer Use-Case-/Aktivitaets-/Sequenzdiagramm)
- Fehlende zentrale Elemente: keine zentralen Datenmodell-Elemente fehlend. Peripher/als
  Entscheidung ausgelassen: Anschrift und Standort inline statt als eigene Wertklassen
  (Adresse/Standort); Bibliotheksausweis als Attribute (kundenID, lichtbild) statt eigener
  Klasse; Ausleihe-/Reservierungsstatus nicht als Enum, sondern aus Assoziationen ableitbar;
  kein eigenes „Bibliothek/Katalog"-Objekt zur Verankerung der Bestandssuche.
- Artefakt-Ebene (nicht K3, aber DoD-relevant): direktes Bild liegt vor
  (`v1-direkt-easylib.png`, 2026-07-07); PlantUML-Rendering liegt vor (2026-07-14).

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: 4, Befunde: gerendert; lesbar, leichte Kreuzungen um Medium/Reservierung/Exemplar.
- Direktes Bild — Score: 4 (vorlaeufig, Selbstbewertung 2026-07-07). Befunde: Werk-/
  Exemplar-/Vorgangs-Ebenen klar getrennt, externe Systeme rechts abgesetzt, keine
  Ueberlappungen; Abzuege: lange Randkante Medium–Reservierung („betrifft") ueber den linken
  Bildrand, zwei nah beieinander laufende Vertikalkanten („umfasst"/„taetigt") zwischen
  Kunde und Exemplar.

## PlantUML vs. direkt – Unterschiede

- Direktes Bild liegt vor (2026-07-07); PlantUML gerendert (2026-07-14), Layout-Vergleich
  daher noch nicht moeglich. Wichtig: Das direkte Bild wurde nachtraeglich aus `v1.puml`
  abgeleitet – inhaltliche Uebereinstimmung ist konstruktionsbedingt und kein unabhaengiger
  Befund; fuer `vergleiche/plantuml-vs-direkt.md`