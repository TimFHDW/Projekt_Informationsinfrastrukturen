# Notizen: easyride / claude / klassendiagramm (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~20:35 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Tim
- Prompt: `prompts/klassendiagramm/easyride-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer die Evaluation (K2/K3): `lastenhefte/easyride.md` (offiziell vorhanden)

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session mit Vorkontext
   (zuvor EasyLib/EasyScoot bearbeitet) -> moeglicher Kontext-Einfluss. Fuer den belastbaren
   KI-/System-Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt (Schritt 1 Verstaendnis-Check, dann Schritt 2) nicht als getrennte
   Nachrichten ausgefuehrt; Diagramm direkt erzeugt.
3. Nur PlantUML-Form erzeugt; die geforderte „direkt gezeichnete" Bildform (`v1-direkt.png`)
   fehlt noch -> Zelle DoD-seitig unvollstaendig.

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich (kein lokales plantuml.jar; Download
  blockiert). `v1-plantuml.png/.svg` fehlt; K1 und K4 daher noch nicht final bewertet.

## Wichtige Modellierungsentscheidungen (Begruendung in evaluation.md)
- `Routenhalt` als eigene Klasse (statt Assoziationsklasse) fuer Reihenfolge ({ordered}) und
  die pro Halt aufzunehmenden/abzusetzenden Fahrgaeste (zwei Assoziationen zu `Fahrgast`).
- `Verbindung` als eigene Klasse zwischen genau zwei Haltepunkten, ungerichtet (Notiz), mit
  `durchschnittlicheFahrzeit`.
- „Zentrale" ueber Attribut `istZentrale : boolean` + Constraint-Notiz modelliert (kein
  eigener Subtyp).
- `Fahrgast` dient zugleich als buchender Kunde (eine Klasse); `Fahrer` und `Tablet` getrennt,
  Kernoperationen des Fahrers am `Fahrer`, `Tablet` als Bedienschnittstelle (Notiz).
- `Flotte` als Aggregation der `Fahrzeuge`.
- Kapazitaetsregel (Fahrgaeste <= Sitzplaetze) und Zentrale-Regel als UML-Constraints/Notizen.
- Kernmethoden verteilt: fahrtBuchen (Fahrgast), wartezeitBerechnen/restfahrzeitBerechnen
  (Fahrt), naechstenHaltepunktAbfragen/ankunftBestaetigen (Fahrer).

## Offene Annahmen / Unklarheiten
- Fahrgast = buchender Kunde in einer Klasse zusammengefasst (Lastenheft nutzt beide Begriffe).
- Keine gemeinsame Personen-Oberklasse fuer Fahrer/Fahrgast (Schritt-2-Vorgabe fordert sie
  nicht; bewusst weggelassen).
- `Fahrt`-`Fahrzeug`-Zuteilung als 0..1 modelliert (zum Buchungszeitpunkt evtl. noch offen).

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easyride.png`)
- Erzeugt am 2026-07-07 (~18:45 CEST) in laufender Cowork-Session (Claude, im Auftrag von
  Linus). Grundlage: Schritt-2-Vorgaben aus `prompts/klassendiagramm/easyride-v1.md` und das
  bereits abgelegte `v1.puml` als Modellbasis (Prompt-Regel: beide Ausgabeformen muessen
  inhaltlich uebereinstimmen).
- Tooling: Claude hat das Bild selbst gezeichnet (eigenes Python/Pillow-Zeichenskript der KI,
  Layout und Koordinaten von der KI bestimmt) – KEINE PlantUML-Beteiligung. PNG 3320x2300 px.
- Methodik-Abweichungen: (1) erneut keine frische, isolierte Session; (2) Bild nicht im selben
  Durchlauf wie der PlantUML-Code entstanden, sondern nachtraeglich aus `v1.puml` abgeleitet –
  die inhaltliche Uebereinstimmung PlantUML vs. direkt ist damit konstruktionsbedingt und
  NICHT als unabhaengiger Befund fuer `vergleiche/plantuml-vs-direkt.md` verwertbar (dort nur
  Zeichenqualitaet/K4 vergleichen); (3) alle drei Klassendiagramm-Bilder in einer Sitzung
  erzeugt -> moeglicher Struktur-Uebertrag zwischen den Systemen.
- Namensabweichung: AGENTS.md/DoD sieht `v1-direkt.png` vor; auf ausdruecklichen Wunsch von
  Linus mit Systemnamen benannt (`v1-direkt-easyride.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session
- [x] `v1-direkt-easyride.png` (direkt generiertes Bild) – nachgeliefert am 2026-07-07,
      siehe Nachtrag oben
- [ ] PlantUML rendern -> `v1-plantuml.png/.svg`; Renderweg notieren
- [ ] K1/K4 in `evaluation.md` finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] Commit: `ergebnis(easyride/claude): klassendiagramm v1 + evaluation`

## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1)

- Neue Dateien: `v2.puml`, `v2-direkt.png` und `v2-plantuml.png` (PNG-Benennung ohne
  Systemnamen, wie bei den Aktivitaets-Zellen; Wunsch Lewin).
- Versionierung: v2 bezeichnet einen ZWEITEN Generierungsdurchlauf mit unveraendertem
  Prompt v1 (auf Wunsch von Lewin, analog zum aktivitaet-v2-Durchlauf vom 14.07.) -
  Abweichung von der Konvention "N = Prompt-Version" (ergebnisse/README.md); fuer
  Vergleiche als Durchlauf-Varianz lesen, nicht als Prompt-Iteration.
- Generierung am 2026-07-14 (~16:35-17:10 CEST) in laufender Cowork-Session (Claude, im
  Auftrag von Lewin); Diagramme direkt in den DoD-Zellen abgelegt.
- Direktbild `v2-direkt.png`: von Claude selbst gezeichnet (eigenes Python/Pillow-
  Zeichenskript, Layout/Koordinaten von der KI bestimmt, KEINE PlantUML-Beteiligung);
  im SELBEN Durchlauf wie `v2.puml` erzeugt (nicht nachtraeglich abgeleitet), beide
  Formen stammen aus demselben Modell -> der inhaltliche Vergleich PlantUML vs. direkt
  ist fuer v2 weiterhin konstruktionsbedingt gleich, verwertbar ist v. a. K4.
- Unabhaengigkeit: `v1.puml` dieser Zelle wurde vor der v2-Generierung bewusst NICHT
  eingesehen; im Sitzungskontext waren allerdings Journal-Eintraege mit
  v1-Kurzbeschreibungen sichtbar -> kein vollstaendig unabhaengiger Durchlauf.
- Methodik-Abweichungen wie bei v1: keine frische isolierte Session; Zweischritt-Prompt
  nicht als getrennte Nachrichten; alle drei v2-Klassendiagramme in einer Sitzung ->
  moeglicher Struktur-Uebertrag zwischen den Systemen.
- Rendering: `v2-plantuml.png` am 2026-07-14 in der Cowork-Sandbox gerendert -
  plantuml.jar 1.2019.06 aus dem npm-Paket node-plantuml (npm in dieser Session wieder
  erreichbar, jar-Direktdownload weiterhin 403; Team-Renderweg vom 06.07.). `v2.puml`
  kompilierte fehlerfrei, keine Korrektur, kein `v2-korrigiert.puml`. PNGs per MD5 +
  PIL-verify geprueft, alle drei Direktbilder visuell abgenommen.
- Inhaltlich v2 (Kurzueberblick): 9 Klassen. Eigene Klasse `Routenhalt` statt Assoziationsklasse - Begruendung:
  Eine Route besucht die Zentrale als Start UND Ende (derselbe Haltepunkt mehrfach in
  einer Route); eine Assoziationsklasse Route-Haltepunkt liesse nur eine Instanz je Paar
  zu. Komposition `Route "1" *-- "2..*" Routenhalt` mit {ordered}; `Verbindung` mit
  Multiplizitaet 2 zu Haltepunkt + Ungerichtet-Notiz; Kapazitaets- und Zentrale-Regel
  als Constraint-Notizen an Route/Fahrzeug; Zustieg/Ausstieg als zwei Assoziationen
  Buchung->Routenhalt (0..1, bis zur Einplanung offen); zweite Route-Routenhalt-
  Assoziation "zuletzt erreichter Halt" fuer die Restfahrzeit. Methoden: fahrtBuchen
  (Fahrgast), wartezeitBerechnenMin/restfahrzeitBerechnenMin (Buchung),
  naechstenHaltAbfragen/ankunftBestaetigen (Route).
- Annahmen der KI in diesem Durchlauf: Fahrgast = buchender Kunde (eine Klasse, Lastenheft nutzt beide Begriffe);
  Fahrer ohne eigene Fachmethoden (Tablet ruft die Routen-Operationen auf, nicht
  modelliert); `kennung` als kuenstlicher Fahrzeug-Identifikator; Ablehnungsfall
  (kein Fahrzeug verfuegbar) nicht modelliert, da im Lastenheft nicht beschrieben;
  `istZentrale : Boolean` statt eigener Subklasse.
- Sichtbare Durchlauf-Varianz gegenueber v1 (erst NACH der Generierung abgeglichen):
  v1 modellierte zusaetzlich Flotte und Tablet sowie die Halt-Fahrgast-
  Zuordnung direkt am Routenhalt und legte Kernmethoden an Fahrer/Fahrt; v2 kommt ohne
  Flotte/Tablet aus, ordnet Zustieg/Ausstieg ueber die Buchung zu und legt die
  Fahrer-Services an der Route ab. Kern (Routenhalt, {ordered}, Verbindung mult 2,
  beide Fachregeln) stabil ueber beide Durchlaeufe.
- Noch offen (v2): vollstaendige K2-K4-Bewertung in `evaluation.md`; Commit macht Lewin
  selbst (ausdruecklicher Wunsch, nichts committet).
