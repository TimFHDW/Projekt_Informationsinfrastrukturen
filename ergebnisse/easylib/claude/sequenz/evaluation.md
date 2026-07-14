# Evaluation: easylib / claude / sequenz

| | |
|---|---|
| Bewertet von | Claude (Cowork) - vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easylib-v1.md` |
| Rendering-Weg | plantuml.jar 1.2019.06 (aus npm-Paket node-plantuml, Cowork-Sandbox), `-charset UTF-8 -tpng` |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 - Syntaktische Korrektheit — Score: 5 (vorlaeufig)

- PlantUML kompiliert ohne Korrektur: **ja** (plantuml.jar 1.2019.06, keine Fehler/Warnungen,
  kein `v1-korrigiert.puml` noetig) -> `v1-plantuml.png`
- Vorbehalt: alte PlantUML-Version; mit dem einheitlichen Team-Renderweg (aktuelle Version)
  gegenpruefen, dann Score finalisieren.
- Struktur: @startuml/@enduml paarig, alt/else/end geschlossen, activate/deactivate paarig,
  create vor erster Nachricht an die Ausleihe - alles korrekt umgesetzt.
- Direktes Bild (`v1-direkt-easylib.png`, Nachtrag 2026-07-07) - UML-Notation korrekt?: ja
  (vorlaeufig): Akteur, Objekt-Lebenslinien mit Aktivierungsbalken, synchrone Aufrufe +
  gestrichelte Antwortpfeile; «create»-Nachricht fuer die neu erzeugte Ausleihe. Bild
  UNABHAENGIG aus dem Prompt erzeugt (NICHT aus v1.puml abgeleitet).

## K2 - Inhaltliche Korrektheit — Score: 4 (vorlaeufig)

Abgleich mit `lastenhefte/easylib.md` und Prompt-Szenario, konkrete Befunde:

- Geforderte Ablaufkette vollstaendig und in richtiger Reihenfolge: Kunde per Kunden-ID
  ermitteln -> Exemplar per ID ermitteln -> Verfuegbarkeit pruefen -> Ausleihe mit
  Leihfrist anlegen -> Status aktualisieren -> Bestaetigung. (ok)
- Verliehen wird das Exemplar, nicht das Werk - konsistent zu Lastenheft und
  Klassendiagramm. (ok)
- Verfuegbarkeitspruefung beruecksichtigt Reservierungen (Medium-Ebene, konsistent
  zum Klassendiagramm). (ok)
- Keine erfundenen Features. (ok)
- Abzug: Leihfrist "28 Tage" ist eine nicht im Lastenheft belegte Annahme (gekennzeichnet);
  mehrere Methoden existieren im Klassendiagramm v1 noch nicht (per Prompt zulaessig und
  ausgewiesen, aber Konsistenzluecke bis zur Ergaenzung).

## K3 - Vollstaendigkeit — Score: 5 (vorlaeufig)

- Mindestanforderung erfuellt (Aufrufe >= 5): ja (8)
- Alle 5 geforderten Lebenslinien vorhanden; create-Nachricht vorhanden;
  Antwortpfeile vorhanden; zusaetzlich Fehlerfall als alt-Fragment.
- Fehlende zentrale Elemente: keine. (Artefakt-Ebene: direkt-Bildform fehlt,
  Rendering steht aus - DoD, nicht K3.)

## K4 - Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: 4 (vorlaeufig), Befunde: klare Links-nach-rechts-Anordnung
  der 5 Lebenslinien; autonumber erleichtert das Zaehlen der Aufrufe; Aktivierungsbalken,
  create-Nachricht und alt-Fragment sauber dargestellt; beide Notizen gut lesbar platziert.
  Abzuege: Antwortpfeil Nr. 9 unbeschriftet (void-Rueckgabe); Selbstaufrufe findeKunde/
  findeExemplar ohne sichtbares Ziel-Objekt (Fassaden-Entwurf, Geschmackssache).
- Direktes Bild — Score: 4 (vorlaeufig, 2026-07-07), Befunde: klare Lebenslinien/
  Aktivierungsbalken, Aufrufe und Antworten gut unterscheidbar; kleiner Abzug: einzelne lange
  Methodensignaturen ragen in enge Nachbar-Spalten. Unabhaengige Bestaetigung ausstehend.

## PlantUML vs. direkt - Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden.

## Was haetten wir anders modelliert?

- Verfuegbarkeitspruefung explizit ausmodellieren (Aufrufe an Ausleihe-/
  Reservierungsobjekte) statt in istVerfuegbar() zu kapseln - detaillierter,
  aber unruhiger.
- Ermittlung von Kunde/Exemplar an eine explizite Repository-/Katalogklasse
  delegieren statt als Selbstaufrufe der Systemfassade.
- Leihfrist als Parameter des Bibliothekars bzw. Konfigurationswert statt
  fester Annahme.

## Sonstige Beobachtungen

- Methodik-Abweichungen (laufende Session, kein Zweischritt-Ablauf, kein
  direkt-Bild): siehe `notizen.md`.

## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1) - Bewertung offen
- `v2.puml` und `v2-direkt.png` liegen vor (s. notizen.md, Nachtrag v2). Diese Datei
  bewertet weiterhin v1; die v2-Bewertung (K1-K4) steht aus, u. a. weil das
  PlantUML-Rendering von `v2.puml` noch fehlt (Umgebung blockiert Renderer, lokal rendern).
- Vorlaeufige Sichtpruefung v2: Mindestanforderungen des Prompts erfuellt (>= 5
  Methodenaufrufe, geforderte Lebenslinien vorhanden, synchrone Aufrufe mit
  Antwortpfeilen, Methodensignaturen mit Parametern).
- easylib-spezifisch: Ausleihe wird per create-Nachricht erzeugt; verliehen wird das
  Exemplar (nicht das Buch) - beide Spezialanforderungen des Prompts erfuellt.
