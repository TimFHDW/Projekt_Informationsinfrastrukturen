# Evaluation: easyride / claude / sequenz

| | |
|---|---|
| Bewertet von | Claude (Cowork) - vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easyride-v1.md` |
| Rendering-Weg | plantuml.jar 1.2019.06 (aus npm-Paket node-plantuml, Cowork-Sandbox), `-charset UTF-8 -tpng` |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 - Syntaktische Korrektheit — Score: 5 (vorlaeufig)

- PlantUML kompiliert ohne Korrektur: **ja** (plantuml.jar 1.2019.06, keine Fehler/Warnungen,
  kein `v1-korrigiert.puml` noetig) -> `v1-plantuml.png`. Vorbehalt: alte PlantUML-Version;
  mit dem einheitlichen Team-Renderweg gegenpruefen.
- Struktur: @startuml/@enduml paarig, loop/end geschlossen, activate/deactivate paarig.
- Direktes Bild (`v1-direkt-easyride.png`, Nachtrag 2026-07-07) - UML-Notation korrekt?: ja
  (vorlaeufig): Akteur als Strichmaennchen, Objekt-Lebenslinien mit Aktivierungsbalken,
  synchrone Aufrufe mit gefuellter Pfeilspitze und gestrichelte Antwortpfeile ueber 5
  Lebenslinien. Bild UNABHAENGIG aus dem Prompt erzeugt (NICHT aus v1.puml abgeleitet).

## K2 - Inhaltliche Korrektheit — Score: 4 (vorlaeufig)

Abgleich mit `lastenhefte/easyride.md` und Prompt-Szenario, konkrete Befunde:

- Geforderte Ablaufkette vollstaendig und in richtiger Reihenfolge: Ankunft bestaetigen ->
  Routenfortschritt aktualisieren -> Ein-/Aussteiger am naechsten Halt ermitteln ->
  Restfahrzeiten der betroffenen Fahrgaeste aktualisieren -> naechster Haltepunkt mit
  Fahrgastnamen ans Tablet. (ok)
- Lastenheft-Treue: Fahrer bestaetigt per Tablet das Erreichen des Haltepunkts; Rueckgabe
  enthaelt naechsten Haltepunkt samt Namen der aufzunehmenden/abzusetzenden Fahrgaeste;
  Restfahrzeit haengt vom zuletzt erreichten Haltepunkt ab (als Note vermerkt). (ok)
- Keine erfundenen Features; die drei Fachregeln (ungerichteter Graph, Sitzplatzgrenze,
  Zentrale) werden nicht verletzt (vom Szenario nicht beruehrt). (ok)
- Abzuege: ankunftBestaetigen() liegt im Klassendiagramm beim Fahrer und wird hier als
  Systemoperation interpretiert (ausgewiesen, aber Konsistenzluecke); drei Route-Methoden
  neu ergaenzt (per Prompt zulaessig); Lebenslinie `fahrt` steht vereinfachend fuer mehrere
  Fahrt-Objekte im loop.

## K3 - Vollstaendigkeit — Score: 5 (vorlaeufig)

- Mindestanforderung erfuellt (Aufrufe >= 5): ja (5 verschiedene, restfahrzeitBerechnen im
  loop mehrfach)
- Alle geforderten Lebenslinien vorhanden (Fahrer/Tablet, System, Route, Fahrt);
  jeder Aufruf mit Antwortpfeil; Signaturen mit Parametern.
- Fehlende zentrale Elemente: keine. (Artefakt-Ebene: direkt-Bildform fehlt - DoD, nicht K3.)

## K4 - Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: 4 (vorlaeufig), Befunde: klare Anordnung der 4 Lebenslinien;
  loop-Fragment mit Bedingungstext und seitlicher Note gut lesbar; autonumber erleichtert
  das Zaehlen; Note mit den zu ergaenzenden Methoden gut platziert. Abzuege: generische
  Antwortbeschriftung "ok" (Nr. 3); seitliche Note ragt rechts ueber das loop-Fragment hinaus.
- Direktes Bild — Score: 4 (vorlaeufig, 2026-07-07), Befunde: klare Lebenslinien/
  Aktivierungsbalken, Aufrufe und Antworten gut unterscheidbar; kleiner Abzug: einzelne lange
  Methodensignaturen ragen in enge Nachbar-Spalten. Unabhaengige Bestaetigung ausstehend.

## PlantUML vs. direkt - Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden.

## Was haetten wir anders modelliert?

- Ein Fahrt-Objekt je betroffenem Fahrgast als eigene Lebenslinie (praeziser) oder explizite
  Multiobjekt-Notation statt einer stellvertretenden Lebenslinie.
- Tablet als eigene Boundary-Lebenslinie zwischen Fahrer und System (im Klassendiagramm
  existiert die Klasse Tablet bereits).
- Routenhalt als eigene Lebenslinie, wenn die Ein-/Aussteiger-Ermittlung detaillierter
  gezeigt werden soll.

## Sonstige Beobachtungen

- Methodik-Abweichungen (laufende Session, kein Zweischritt-Ablauf, kein direkt-Bild,
  Typ-interner Kontext-Bleed zwischen den drei Systemen): siehe `notizen.md`.
