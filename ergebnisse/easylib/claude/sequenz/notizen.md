# Notizen: easylib / claude / sequenz (v1)

Roh-Beobachtungen aus der Generierung. Ergaenzt die strukturierte Bewertung in `evaluation.md`.

## Rahmen
- Datum/Zeit: 2026-07-06 (CEST)
- KI: Claude (Anthropic), genutzt ueber Cowork (Claude-Desktop), im Auftrag von Basti
- Prompt: `prompts/sequenz/easylib-v1.md` (Schritt 1 Basis + Schritt 2 Diagramm)
- Referenz fuer Evaluation (K2/K3): `lastenhefte/easylib.md`

## Methodik-Abweichungen (wichtig fuer die Reflexion)
1. Keine frische, isolierte Session: Generierung in laufender Cowork-Session mit Vorkontext
   (Repo-Regeln, Klassendiagramm easylib/claude v1 und Lastenheft bereits im Kontext).
   Moeglicher Kontext-Einfluss -> fuer belastbaren Vergleich in frischer Session reproduzieren.
   Hinweis: Der Vorkontext beguenstigt hier die vom Prompt geforderte Namenskonsistenz
   zum Klassendiagramm.
2. Zweistufiger Prompt nicht als zwei getrennte Nachrichten mit Verstaendnis-Check ausgefuehrt.
3. Nur PlantUML-Form: die geforderte "direkt gezeichnete" Bildform (`v1-direkt.png`) wurde
   nicht erzeugt -> Zelle DoD-seitig unvollstaendig.

## Selbst-Check gegen Prompt-Anforderungen
- >= 5 Methodenaufrufe: ja (8: verleiheExemplar, findeKunde, findeExemplar, istVerfuegbar,
  ausleihen, create Ausleihe, registriereAusleihe, aktualisiereStatus)
- Ausleihe per create-Nachricht: ja
- Exemplar (nicht Buch) wird verliehen: ja
- Alle geforderten Lebenslinien vorhanden: Bibliothekar, EasyLib, Kunde, Exemplar, Ausleihe
- Synchrone Aufrufe mit Antwortpfeilen und Signaturen mit Parametern: ja

## Modellierungsentscheidungen / Annahmen
- Konsistenz zum Klassendiagramm v1: `Exemplar.istVerfuegbar()` und `Exemplar.ausleihen(kunde)`
  unveraendert uebernommen.
- Im Klassendiagramm gedanklich zu ergaenzen (per Prompt zulaessig, als Note im Diagramm
  ausgewiesen): Systemfassade `EasyLib` mit verleiheExemplar/findeKunde/findeExemplar,
  `Kunde.registriereAusleihe()`, `Exemplar.aktualisiereStatus()`, Konstruktor der Ausleihe.
- Annahme Leihfrist: 28 Tage ab Ausleihdatum (Lastenheft nennt keine Dauer).
- Verfuegbarkeitspruefung in `istVerfuegbar()` gekapselt: nicht verliehen UND keine
  entgegenstehende Reservierung (Reservierung gemaess Klassendiagramm auf Medium-Ebene).
- alt-Fragment fuer den Fehlerfall ergaenzt - im Prompt nicht gefordert, aber fachlich sinnvoll.
- Die Leihfrist-Mehrdeutigkeit des Lastenhefts betrifft die Verlaengerung, nicht die
  Neuausleihe - fuer dieses Szenario nicht einschlaegig.

## Rendering / Tooling
- Gerendert am 2026-07-06 in der Cowork-Sandbox (Linux): plantuml.jar **1.2019.06**
  (mitgeliefert im npm-Paket `node-plantuml`), Aufruf:
  `java -jar plantuml.jar -charset UTF-8 -tpng v1.puml` -> `v1-plantuml.png`.
- Hintergrund: Direkte Downloads (github.com, Maven Central) sind in der Sandbox blockiert,
  apt ohne Root nicht nutzbar; npm funktioniert - daher der Umweg ueber `node-plantuml`.
- `v1.puml` kompilierte **ohne Korrektur** (kein `v1-korrigiert.puml` noetig).
- Achtung: 1.2019.06 ist eine alte PlantUML-Version. Fuer den einheitlichen Team-Renderweg
  ggf. mit aktueller Version nachrendern und Ergebnis vergleichen.
- Kleine Beobachtung im Rendering: Antwortpfeil Nr. 9 (kunde --> ausleihe) ist unbeschriftet
  (so im Original-Code, void-Rueckgabe) - kein Fehler, nur kosmetisch.

## Nachtrag 2026-07-07: direkt generiertes Bild (`v1-direkt-easylib.png`)
- Erzeugt am 2026-07-07 in laufender Cowork-Session (Claude, im Auftrag von Tim), allein aus
  `prompts/sequenz/easylib-v1.md` (Schritt-1-Systembeschreibung + Schritt-2-Szenario). Die
  zugehoerige `v1.puml` wurde auf Anweisung von Tim BEWUSST NICHT angesehen.
- Folge (wichtig): Das Bild ist eine UNABHAENGIGE Generierung aus dem Prompt, NICHT aus der
  `v1.puml` abgeleitet (anders als die Klassendiagramm-/Use-Case-Direktbilder vom 07.07.).
  Damit ist `vergleiche/plantuml-vs-direkt.md` fuer diese Zelle auch inhaltlich belastbar,
  nicht nur bei der Zeichenqualitaet (K4).
- Tooling: eigener Sequenzdiagramm-Generator (Python) -> SVG -> PNG via librsvg-2 + cairo
  (ctypes), 1360 px breit (2x), weisser Hintergrund. Visuell verifiziert.
- Inhalt: Szenario „Bibliothekar verleiht ein Buchexemplar an einen Kunden", 5 Lebenslinien
  (Bibliothekar, EasyLib-System, Kunde, Exemplar, Ausleihe), 6 Aufrufe inkl. «create» der
  Ausleihe; verliehen wird das Exemplar (nicht das Buch).
- Methodik-Abweichungen: (1) keine frische, isolierte Session; (2) Zweischritt-Prompt nicht als
  getrennte Nachrichten; (3) alle drei Sequenzbilder in einer Session.
- Namensabweichung: AGENTS.md/DoD nennt `vN-direkt.png`; auf Wunsch von Tim mit Systemnamen
  (`v1-direkt-easylib.png`).

## Noch zu tun (DoD)
- [ ] Reproduktion in frischer, isolierter Session (Methodik)
- [x] `v1-direkt-easylib.png` ergaenzt am 2026-07-07 (unabhaengig aus Prompt, siehe Nachtrag)
- [x] PlantUML rendern -> `v1-plantuml.png` (Weg siehe oben)
- [ ] K4 fuer direktes Bild offen; K1/K4-PlantUML vorlaeufig bewertet; K2/K3 unabhaengig bestaetigen
- [ ] Matrix + Journal + Commit
