# Evaluation: easylib / claude / sequenz

| | |
|---|---|
| Bewertet von | Claude (Cowork) - vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
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
- Direktes Bild - UML-Notation korrekt?: n. v. (keine direkt-Bildform erzeugt)

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
- Direktes Bild — Score: n. v., Befunde: keine direkt