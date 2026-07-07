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

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [ ] `v1-direkt.png` nachliefern
- [x] PlantUML rendern -> `v1-plantuml.png` (Weg siehe oben)
- [ ] K4 fuer direktes Bild offen; K2/K3 unabhaengig bestaetigen
- [ ] Matrix + Journal + Commit
