# Evaluation: easyscoot / claude / sequenz

| | |
|---|---|
| Bewertet von | Claude (Cowork) - vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 (v1.puml); Nachtrag direktes Bild: 2026-07-07 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/sequenz/easyscoot-v1.md` |
| Rendering-Weg | plantuml.jar 1.2019.06 (aus npm-Paket node-plantuml, Cowork-Sandbox), `-charset UTF-8 -tpng` |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 - Syntaktische Korrektheit — Score: 5 (vorlaeufig)

- PlantUML kompiliert ohne Korrektur: **ja** (plantuml.jar 1.2019.06, keine Fehler/Warnungen,
  kein `v1-korrigiert.puml` noetig) -> `v1-plantuml.png`. Vorbehalt: alte PlantUML-Version;
  mit dem einheitlichen Team-Renderweg gegenpruefen.
- Struktur: @startuml/@enduml paarig, activate/deactivate paarig, Stereotyp
  <<external system>> am Rechnungssystem.
- Direktes Bild (`v1-direkt-easyscoot.png`, Nachtrag 2026-07-07) - UML-Notation korrekt?: ja
  (vorlaeufig): Akteur, Objekt-Lebenslinien mit Aktivierungsbalken, synchrone Aufrufe +
  gestrichelte Antwortpfeile ueber 5 Lebenslinien inkl. Rechnungssystem (Preisberechnung dort).
  Bild UNABHAENGIG aus dem Prompt erzeugt (NICHT aus v1.puml abgeleitet).

## K2 - Inhaltliche Korrektheit — Score: 4 (vorlaeufig)

Abgleich mit `lastenhefte/easyscoot.md` und Prompt-Szenario, konkrete Befunde:

- Geforderte Ablaufkette vollstaendig und in richtiger Reihenfolge: Nutzung beenden ->
  E-Scooter sperren/Status aktualisieren -> Fahrtdaten ermitteln -> Preis vom
  Rechnungssystem -> Zusammenfassung an den Kunden. (ok)
- Lastenheft-Treue: Beenden per Smartphone; Zusammenfassung mit Dauer, gefahrenen
  Kilometern, verbrauchten Wattstunden und Preis; Preisberechnung durch das existierende,
  nur angebundene Rechnungssystem (externe Lebenslinie, EasyScoot rechnet nicht selbst). (ok)
- Leihstatus-Wechsel auf NICHT_IN_BENUTZUNG konsistent zum Enum des Klassendiagramms. (ok)
- Keine erfundenen Features (keine Bezahlfunktion, kein Bewertungssystem). (ok)
- Abzuege: nutzungBeenden() liegt im Klassendiagramm beim Kunden und wird hier als
  Systemoperation interpretiert (ausgewiesen, aber Konsistenzluecke); sperren() der
  Mobilfunk-Software ist im Lastenheft nicht woertlich beschrieben (plausible Ableitung
  aus Freischalten/Wartungs-Abmeldung); Annahme, dass Fahrtdaten bereits aggregiert
  vorliegen.

## K3 - Vollstaendigkeit — Score: 5 (vorlaeufig)

- Mindestanforderung erfuellt (Aufrufe >= 5): ja (6)
- Alle 5 geforderten Lebenslinien vorhanden (Kunde/App, System, E-Scooter, Fahrt,
  Rechnungssystem); jeder Aufruf mit Antwortpfeil; Signaturen mit Parametern.
- Fehlende zentrale Elemente: keine. (Artefakt-Ebene: direkt-Bildform fehlt - DoD, nicht K3.)

## K4 - Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: 4 (vorlaeufig), Befunde: 5 Lebenslinien klar angeordnet,
  Stereotyp <<external system>> am Rechnungssystem sichtbar; Selbstaufruf (Nr. 4) sauber
  dargestellt; Zeilenumbrueche in langen Nachrichten verhindern Ueberbreite. Abzuege:
  generische Antwortbeschriftung "ok" (Nr. 10); Antwort-Labels stilistisch gemischt
  (Werte vs. Bestaetigungen).
- Direktes Bild — Score: 4 (vorlaeufig, 2026-07-07), Befunde: klare Lebenslinien/
  Aktivierungsbalken, Aufrufe und Antworten gut unterscheidbar; kleiner Abzug: einzelne lange
  Methodensignaturen ragen in enge Nachbar-Spalten. Unabhaengige Bestaetigung ausstehend.

## PlantUML vs. direkt - Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden.

## Was haetten wir anders modelliert?

- Signaturkonflikt Prompt vs. Klassendiagramm (berechnePreis) im Klassendiagramm v2
  aufloesen, statt ihn nur im Sequenzdiagramm zu entscheiden.
- Zusammenfassung als eigenes Rueckgabeobjekt (DTO) modellieren statt als Aufzaehlung
  im Antwortpfeil.
- Optional asynchrone Mobilfunk-Kommunikation zum E-Scooter (async-Pfeil) statt synchronem
  sperren() - realistischer, aber der Prompt fordert synchrone Aufrufe.

## Sonstige Beobachtungen

- Methodik-Abweichungen (laufende Session, kein Zweischritt-Ablauf, kein direkt-Bild,
  Typ-interner Kontext-Bleed zwischen den drei Systemen): siehe `notizen.md`.
