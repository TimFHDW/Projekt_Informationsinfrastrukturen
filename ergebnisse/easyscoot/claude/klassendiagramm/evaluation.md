# Evaluation: easyscoot / claude / klassendiagramm

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyscoot-v1.md` |
| Rendering-Weg | PlantUML am 2026-07-14 gerendert (plantuml.jar/lokal); Direktbild s. Nachtrag |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

> Quelle fuer K2/K3: `lastenhefte/easyscoot.md`.

## K1 – Syntaktische Korrektheit — Score: PlantUML 5 / direkt 5 (gerendert 2026-07-14, kompiliert fehlerfrei)
- PlantUML kompiliert ohne Korrektur: ja - am 2026-07-14 fehlerfrei gerendert, keine Korrektur noetig.
- Struktur-Vorpruefung: `@startuml/@enduml` paarig, alle `note`-Bloecke geschlossen, 3 Enums,
  Vererbung `Nutzer <|-- {Kunde, Flottenmanager, Service-Mitarbeiter}`, jede Assoziation mit
  Multiplizitaeten (Ausnahme: Abhaengigkeit `Fahrt ..> Rechnungssystem`, bewusst ohne).
- Direktes Bild (`v1-direkt-easyscoot.png`, Nachtrag 2026-07-07) – UML-Notation korrekt?:
  ja (vorlaeufige Selbstbewertung): abstrakte Klasse `Nutzer` kursiv, Vererbung mit hohlem
  Dreieck, drei `«enumeration»`-Boxen, `«external system»`-Stereotyp, Abhaengigkeit
  Fahrt ..> Rechnungssystem gestrichelt mit offener Pfeilspitze, Multiplizitaeten an allen
  Assoziationen, abgeleitetes Attribut mit `/`-Praefix. Einschraenkung: Bild nachtraeglich
  aus `v1.puml` abgeleitet (siehe notizen.md, Nachtrag).

## K2 – Inhaltliche Korrektheit — Score: 5 (vorlaeufig)

Abgleich mit `lastenhefte/easyscoot.md`, konkrete Befunde:

- Geforderte Klassen vorhanden: Kunde, E-Scooter, Fahrt, Flottenmanager, Service-Mitarbeiter,
  Rechnungssystem (extern) (+ Nutzer, Flotte, Ladestation, Position). ✓
- Alle genannten Attribute mit Datentypen uebernommen: Kunde (Vorname, Name, Strasse,
  Hausnummer, PLZ, Ort, Email), E-Scooter (ID, Marke, Modell, Batteriekapazitaet Wh,
  Verbrauchskoeffizient Wh/km, Position, Ladestand, Fahr-/Leih-/Wartungsstatus), Fahrt
  (Dauer, gefahrene Kilometer, verbrauchte Wattstunden, Preis). ✓
- Fahr-/Leih-/Wartungsstatus als Enumerationen mit den Lastenheft-Werten. ✓
- `Rechnungssystem` als «external system» / Schnittstelle, nicht als normale Systemklasse. ✓
- Gemeinsame Oberklasse `Nutzer` fuer die drei Rollen, wie gefordert geprueft und begruendet. ✓
- Kernmethoden vorhanden (buchen, freischalten, nutzungBeenden, wartungStarten/-Beenden). ✓
- Keine erfundenen Features. ✓

## K3 – Vollstaendigkeit — Score: 4 (vorlaeufig)

- Mindestanforderung (UC ≥ 5 / Aktivitaeten ≥ 5 / Aufrufe ≥ 5): n. a. (nur andere Diagrammtypen).
- Fehlende zentrale Elemente: keine. Ergaenzt (aus dem Lastenheft ableitbar): `Flotte`,
  `Ladestation`, `Position`. Bewusst offen gelassen: „geschaetzte uebrige Fahrzeit" als
  abgeleitetes Attribut statt gespeichert; Mobilfunk-Anbindung nur als Notiz, nicht als Klasse.
- Artefakt-Ebene (DoD): direktes Bild liegt vor (`v1-direkt-easyscoot.png`, 2026-07-07);
  PlantUML-Rendering liegt vor (2026-07-14).

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: 4, Befunde: gerendert; breit, aber klar; wenige lange Kanten, keine Ueberlappungen.
- Direktes Bild — Score: 4 (vorlaeufig, Selbstbewertung 2026-07-07). Befunde: klare Spalten
  (Rollen oben, Domaene Mitte, Enums rechts), Vererbungsbus sauber, keine Ueberlappungen;
  Abzuege: EScooter-Notiz und Positions-/Ladestation-Kante