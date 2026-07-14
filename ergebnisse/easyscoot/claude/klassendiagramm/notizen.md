# Notizen: easyscoot / claude / klassendiagramm (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06, ~20:40 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Tim
- Prompt: `prompts/klassendiagramm/easyscoot-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer die Evaluation (K2/K3): `lastenhefte/easyscoot.md` (offiziell vorhanden)

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session mit Vorkontext
   (zuvor EasyLib/EasyRide bearbeitet) -> moeglicher Kontext-Einfluss. Fuer den belastbaren
   KI-/System-Vergleich in frischer Session reproduzieren.
2. Zweistufiger Prompt (Verstaendnis-Check, dann Diagramm) nicht als getrennte Nachrichten
   ausgefuehrt; Diagramm direkt erzeugt.
3. Nur PlantUML-Form erzeugt; „direkt gezeichnete" Bildform (`v1-direkt.png`) fehlt noch
   -> Zelle DoD-seitig unvollstaendig.

## Rendering / Tooling
- Kein PlantUML-Rendering in dieser Umgebung moeglich (kein lokales plantuml.jar; Download
  blockiert). `v1-plantuml.png/.svg` fehlt; K1 und K4 daher noch nicht final bewertet.

## Wichtige Modellierungsentscheidungen (Begruendung in evaluation.md)
- Gemeinsame abstrakte Oberklasse `Nutzer` fuer `Kunde`, `Flottenmanager` und
  `Service-Mitarbeiter` (alle mit Nutzerkonto) – wie im Prompt zur Pruefung gestellt.
- `Fahrstatus`, `Leihstatus`, `Wartungsstatus` als Enumerationen mit den Lastenheft-Werten.
- `Rechnungssystem` als «external system» mit Abhaengigkeit von `Fahrt` (nur angebunden,
  berechnet den Preis).
- `Fahrt` traegt Dauer, gefahrene Kilometer, verbrauchte Wattstunden und Preis und verbindet
  `Kunde` und `EScooter`.
- `Flotte` als Aggregation der `EScooter`; `Ladestation` und `Position` als eigene Klassen.
- `geschaetzteRestfahrzeit` als abgeleitetes Attribut (`/`) am `EScooter` markiert.

## Offene Annahmen / Unklarheiten
- `Nutzer`-Oberklasse mit minimalem gemeinsamem Attribut (`nutzername`); rollenspezifische
  Daten liegen in den Unterklassen (nur `Kunde` ist im Lastenheft datenreich beschrieben).
- `Position` als eigene Wertklasse (Breite/Laenge); im Lastenheft nur „Position" genannt.
- `ladestand` als Prozentwert (int) interpretiert (Filter „<= 50 %").
- Buchen/Freischalten/Beenden am `Kunde`, Wartungsmodus am `Service-Mitarbeiter` platziert.

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easyscoot.png`)
- Erzeugt am 2026-07-07 (~18:45 CEST) in laufender Cowork-Session (Claude, im Auftrag von
  Linus). Grundlage: Schritt-2-Vorgaben aus `prompts/klassendiagramm/easyscoot-v1.md` und das
  bereits abgelegte `v1.puml` als Modellbasis (Prompt-Regel: beide Ausgabeformen muessen
  inhaltlich uebereinstimmen).
- Tooling: Claude hat das Bild selbst gezeichnet (eigenes Python/Pillow-Zeichenskript der KI,
  Layout und Koordinaten von der KI bestimmt) – KEINE PlantUML-Beteiligung. PNG 3560x2500 px.
- Methodik-Abweichungen: (1) erneut keine frische, isolierte Session; (2) Bild nicht im selben
  Durchlauf wie der PlantUML-Code entstanden, sondern nachtraeglich aus `v1.puml` abgeleitet –
  die inhaltliche Uebereinstimmung PlantUML vs. direkt ist damit konstruktionsbedingt und
  NICHT als unabhaengiger Befund fuer `vergleiche/plantuml-vs-direkt.md` verwertbar (dort nur
  Zeichenqualitaet/K4 vergleichen); (3) alle drei Klassendiagramm-Bilder in einer Sitzung
  erzeugt -> moeglicher Struktur-Uebertrag zwischen den Systemen.
- Namensabweichung: AGENTS.md/DoD sieht `v1-direkt.png` vor; auf ausdruecklichen Wunsch von
  Linus mit Systemnamen benannt (`v1-direkt-easyscoot.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session
- [x] `v1-direkt-easyscoot.png` (direkt generiertes Bild) – nachgeliefert am 2026-07-07,
      siehe Nachtrag oben
- [ ] PlantUML rendern -> `v1-plantuml.png/.svg`; Renderweg notieren
- [ ] K1/K4 in `evaluation.md` finalisieren; K2/K3 unabhaengig bestaetigen
- [ ] Commit: `ergebnis(easyscoot/claude): klassendiagramm v1 + evaluation`

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
- Inhaltlich v2 (Kurzueberblick): Abstrakte Oberklasse `Nutzerkonto` fuer Kunde/Flottenmanager/
  ServiceMitarbeiter - bewusst OHNE eigene Attribute (nur fuer Kunden sind im Lastenheft
  Attribute spezifiziert; Begruendung als Notiz im Diagramm). Drei Enumerationen
  Fahrstatus/Leihstatus/Wartungsstatus mit den Lastenheft-Werten; `Rechnungssystem` als
  interface «extern» mit Abhaengigkeit `Fahrt ..> Rechnungssystem` + Notiz (Preis wird
  extern berechnet); alle Lastenheft-Attribute mit Datentypen am EScooter/Kunde/Fahrt;
  Methoden: Buchen/Freischalten/Beenden am Kunden, Gesamtliste/Niedrigladungsliste/
  Wartungsmodus/Aufnehmen/Ausmustern an den Rollen, statusdatenMelden/
  restfahrzeitSchaetzenMin/freischalten/sperren/mobilfunkAn-/Abmelden am EScooter.
- Annahmen der KI in diesem Durchlauf: `GeoPosition` als nicht weiter modellierter Datentyp; `ladezustandProzent`
  als Prozentwert (Filter "<= 50 %"); Restfahrzeit als Methode (aus Ladezustand,
  Batteriekapazitaet und Verbrauchskoeffizient ableitbar) statt gespeichertem Attribut;
  `preis` wird vom externen Rechnungssystem geliefert und an der Fahrt gespeichert;
  sperren() als Gegenstueck zum Freischalten beim Nutzungsende.
- Sichtbare Durchlauf-Varianz gegenueber v1 (erst NACH der Generierung abgeglichen):
  v1 fuehrte zusaetzlich Flotte, Ladestation und Position als Klassen, gab der
  Oberklasse (dort `Nutzer`) ein Attribut `nutzername` und markierte die Restfahrzeit
  als abgeleitetes Attribut; v2 verzichtet auf diese Zusatzklassen, laesst die
  Oberklasse attributlos und modelliert die Restfahrzeit als Methode. Kern (Enums,
  externe Schnittstelle, Attributabdeckung, Oberklassen-Entscheidung) stabil.
- Noch offen (v2): vollstaendige K2-K4-Bewertung in `evaluation.md`; Commit macht Lewin
  selbst (ausdruecklicher Wunsch, nichts committet).
