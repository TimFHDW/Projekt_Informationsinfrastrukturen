# Notizen: easyride / claude / sequenz (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Basti
- Prompt: `prompts/sequenz/easyride-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer Evaluation (K2/K3): `lastenhefte/easyride.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session mit erheblichem
   Vorkontext (Repo-Regeln, Klassendiagramm easyride/claude v1, Lastenheft sowie die zuvor
   erzeugte easylib-Sequenz-Zelle im Kontext). Moeglicher Kontext-Einfluss -> fuer belastbaren
   Vergleich in frischer Session reproduzieren. Der Vorkontext beguenstigt die geforderte
   Namenskonsistenz zum Klassendiagramm.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (`v1-direkt.png`) wurde
   nicht erzeugt -> Zelle DoD-seitig unvollstaendig.
4. Gleiche Sitzung erzeugte easylib-, easyride- und easyscoot-Sequenz -> auch Typ-interner
   Kontext-Bleed zwischen den Systemen moeglich (aehnliche Fassaden-Struktur der Diagramme).

## Selbst-Check gegen Prompt-Anforderungen
- >= 5 Methodenaufrufe: ja (5 verschiedene: ankunftBestaetigen, fortschrittAktualisieren,
  naechsterHalt, fahrgaesteAmHalt, restfahrzeitBerechnen; letzterer im loop je Fahrgast)
- Jeder synchrone Aufruf mit Antwortpfeil: ja
- Geforderte Lebenslinien vorhanden: Fahrer (Tablet), EasyRide-System, Route, Fahrt
- Namen konsistent zum Klassendiagramm v1: Route, Routenhalt, Haltepunkt,
  Fahrt.restfahrzeitBerechnen()

## Modellierungsentscheidungen / Annahmen
- `Fahrt.restfahrzeitBerechnen()` unveraendert aus dem Klassendiagramm uebernommen;
  "Aktualisieren" der Restfahrzeit = Neuberechnung ausgehend vom zuletzt erreichten
  Haltepunkt (entspricht Lastenheft-Formulierung).
- Im Klassendiagramm gedanklich zu ergaenzen (per Prompt zulaessig, als Note ausgewiesen):
  Systemfassade `EasyRide` mit ankunftBestaetigen(haltepunkt); Route.fortschrittAktualisieren(),
  Route.naechsterHalt(), Route.fahrgaesteAmHalt(). Hinweis: ankunftBestaetigen() ist im
  Klassendiagramm als Methode des Fahrers modelliert - fuer das Sequenzdiagramm als
  Systemoperation interpretiert (Akteur ruft System auf).
- Vereinfachung: Die Lebenslinie `fahrt : Fahrt` steht im loop stellvertretend fuer die
  Fahrten mehrerer betroffener Fahrgaeste (uebliche, aber vereinfachende Praxis).
- Die drei unverhandelbaren Fachregeln (ungerichteter Graph, Sitzplatzgrenze, Zentrale)
  werden vom Szenario nicht beruehrt und nicht verletzt.

## Rendering / Tooling
- Gerendert am 2026-07-06 in der Cowork-Sandbox (Linux): plantuml.jar **1.2019.06**
  (mitgeliefert im npm-Paket `node-plantuml`), Aufruf:
  `java -jar plantuml.jar -charset UTF-8 -tpng v1.puml` -> `v1-plantuml.png`.
- `v1.puml` kompilierte **ohne Korrektur** (kein `v1-korrigiert.puml` noetig).
- Achtung: 1.2019.06 ist eine alte PlantUML-Version. Fuer den einheitlichen Team-Renderweg
  ggf. mit aktueller Version nachrendern und Ergebnis vergleichen.

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easyride.png`)
- Erzeugt am 2026-07-07 in laufender Cowork-Session (Claude, im Auftrag von Tim), allein aus
  `prompts/sequenz/easyride-v1.md` (Schritt-1-Systembeschreibung + Schritt-2-Szenario). Die
  zugehoerige `v1.puml` wurde auf Anweisung von Tim BEWUSST NICHT angesehen.
- Folge (wichtig): Das Bild ist eine UNABHAENGIGE Generierung aus dem Prompt, NICHT aus der
  `v1.puml` abgeleitet (anders als die Klassendiagramm-/Use-Case-Direktbilder vom 07.07.).
  Damit ist `vergleiche/plantuml-vs-direkt.md` fuer diese Zelle auch inhaltlich belastbar,
  nicht nur bei der Zeichenqualitaet (K4).
- Tooling: eigener Sequenzdiagramm-Generator (Python) -> SVG -> PNG via librsvg-2 + cairo
  (ctypes), 1360 px breit (2x), weisser Hintergrund. Visuell verifiziert.
- Inhalt: Szenario „Fahrer bestaetigt Erreichen eines Haltepunkts", 5 Lebenslinien (Fahrer,
  Tablet, EasyRide-System, Route, Fahrt), 6 synchrone Aufrufe mit Antwortpfeilen.
- Methodik-Abweichungen: (1) keine frische, isolierte Session; (2) Zweischritt-Prompt nicht als
  getrennte Nachrichten; (3) alle drei Sequenzbilder in einer Session.
- Namensabweichung: AGENTS.md/DoD nennt `vN-direkt.png`; auf Wunsch von Tim mit Systemnamen
  (`v1-direkt-easyride.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] `v1-direkt-easyride.png` ergaenzt am 2026-07-07 (unabhaengig aus Prompt, siehe Nachtrag)
- [x] PlantUML rendern -> `v1-plantuml.png` (Weg siehe oben)
- [ ] K4 fuer direktes Bild offen; K2/K3 unabhaengig bestaetigen
- [ ] Matrix + Journal + Commit

## Nachtrag 2026-07-14: v2 (2. Durchlauf, Prompt v1)
- Neue Dateien: `v2.puml` und `v2-direkt.png` (Benennung ohne Systemnamen, wie bei den
  Aktivitaetsdiagramm-Zellen vom 14.07.).
- Versionierung: v2 bezeichnet einen ZWEITEN Generierungsdurchlauf mit unveraendertem
  Prompt v1 (auf Wunsch von Linus) - Abweichung von der Konvention "N = Prompt-Version"
  (ergebnisse/README.md); fuer Vergleiche als Durchlauf-Varianz lesen, nicht als
  Prompt-Iteration.
- Generierung am 2026-07-14 (~16:10-16:40 CEST) in laufender Cowork-Session (Claude, im
  Auftrag von Linus). KI-Ausgabe unveraendert abgelegt.
- Direktbild `v2-direkt.png`: von Claude selbst gezeichnet (eigenes Python/Pillow-
  Zeichenskript, Layout/Koordinaten von der KI bestimmt, keine PlantUML-Beteiligung);
  im SELBEN Durchlauf wie `v2.puml` erzeugt, beide Formen stammen aus demselben Modell.
  Nach Sichtpruefung der ersten Fassung wurden zwei zu lange Nachrichtenbeschriftungen
  VOR der Ablage umgebrochen (nur Zeilenumbruch im Bild, keine inhaltliche Aenderung;
  `v2.puml` davon unberuehrt).
- Methodik-Abweichungen wie bei v1: keine frische isolierte Session (Vorkontext u. a.
  v1-Zellen und die aktivitaet-v2-Nachtraege); Zweischritt-Prompt nicht als getrennte
  Nachrichten mit Verstaendnis-Check; alle drei v2-Sequenzdiagramme in einer Sitzung ->
  moeglicher Struktur-Uebertrag zwischen den Systemen.
- Kein `v2-plantuml.png`: PlantUML-Rendering in der Cowork-Umgebung weiterhin blockiert
  (am 14.07. erneut geprueft: npm 403, kein jar verfuegbar); bitte lokal rendern wie bei v1.
- Inhaltlich vs. v1: `buchung : Buchung` als vierte Lebenslinie statt `fahrt : Fahrt`
  (der Prompt nennt "Buchung/Fahrt"); Restfahrzeit-Aktualisierung im loop ueber die
  Buchungen; andere Fassaden-/Methodennamen als v1 (halteErreicht/aktualisiereFortschritt/
  ermittleNaechstenHalt/ermittleEinUndAussteiger statt ankunftBestaetigen/
  fortschrittAktualisieren/naechsterHalt/fahrgaesteAmHalt) -> Namenskonsistenz zum
  Klassendiagramm v1 NICHT gegeben; die Methoden sind (per Prompt zulaessig) als im
  Klassendiagramm zu ergaenzend ausgewiesen (Note im Diagramm). 5 verschiedene
  Methodenaufrufe, 10 Nachrichten gesamt, alle synchronen Aufrufe mit Antwortpfeil.
