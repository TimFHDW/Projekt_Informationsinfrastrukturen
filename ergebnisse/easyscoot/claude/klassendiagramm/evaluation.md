# Evaluation: easyscoot / claude / klassendiagramm

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/klassendiagramm/easyscoot-v1.md` |
| Rendering-Weg | ausstehend – in dieser Session kein PlantUML-Rendering moeglich |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

> Quelle fuer K2/K3: `lastenhefte/easyscoot.md`.

## K1 – Syntaktische Korrektheit — Score: offen (Rendering ausstehend)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft – kein Renderlauf moeglich.
  Im Team-Renderweg pruefen und Ergebnis hier eintragen.
- Struktur-Vorpruefung: `@startuml/@enduml` paarig, alle `note`-Bloecke geschlossen, 3 Enums,
  Vererbung `Nutzer <|-- {Kunde, Flottenmanager, Service-Mitarbeiter}`, jede Assoziation mit
  Multiplizitaeten (Ausnahme: Abhaengigkeit `Fahrt ..> Rechnungssystem`, bewusst ohne).
- Direktes Bild – UML-Notation korrekt?: n. v. – keine „direkt"-Bildform erzeugt.

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
- Artefakt-Ebene (DoD): „direkt"-Bildform fehlt; Rendering steht aus.

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: offen, Befunde: noch nicht gerendert.
- Direktes Bild — Score: n. v.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden, kein direktes Bild, kein Rendering.

## Was haetten wir anders modelliert?

- `Nutzer`/`Nutzerkonto` ggf. als getrennte Klassen (Konto vs. Person).
- `Position` alternativ als einfaches Attribut statt eigener Klasse.
- Mobilfunk-Telemetrie als eigene «external system»-Schnittstelle explizit machen.
- Leihstatus/Wartungsstatus ggf. als Zustandsautomat (State Machine) statt Enum.

## Sonstige Beobachtungen

- Methodik-Abweichung: Generierung in laufender Cowork-Session, nicht in frischer, isolierter
  Chat-Session -> moeglicher Kontext-Einfluss; fuer belastbaren Vergleich reproduzieren.
- Zweistufiger Prompt nicht getrennt ausgefuehrt; Diagramm direkt erzeugt.
- Details siehe `notizen.md`.
