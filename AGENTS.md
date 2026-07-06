# AGENTS.md – Anweisungen für KI-Agenten

Du arbeitest im Abgabe-Repo der Projektarbeit **„Modellierung mit KI – Multi-Case-Study mit UML"**
(Modul Informationsinfrastrukturen, FHDW, Q3-2026, Prof. Dr. Jil Klünder).
Bearbeitungszeitraum: 07.–19.07.2026 · Präsentation: 20.07.2026.

## Worum es geht

Aus den Lastenheften dreier Systeme (**EasyRide, EasyScoot, EasyLib**) werden mit drei KIs
(**Claude, ChatGPT, Gemini**) vier UML-Diagrammtypen generiert – jeweils in zwei Formaten:

1. **direkt** – das von der KI selbst gezeichnete/generierte Diagramm (Bild)
2. **plantuml** – der von der KI gelieferte PlantUML-Code, den wir selbst rendern

Alle Artefakte werden einheitlich evaluiert (Syntax, Inhalt, Vollständigkeit, Lesbarkeit) und
verglichen: KI vs. KI, System vs. System, PlantUML vs. direkt, Diagrammtyp vs. Diagrammtyp,
Prompt-Version vs. Prompt-Version.

**Benotet werden:** das Erzeugnis (25 % der Modulnote), die Präsentation (25 %) – und ausdrücklich
auch die **Vorgehensdokumentation, die Reflexion und die Git-Historie** („echte Versionierung,
nicht nur initialer und finaler Commit").

## Goldene Regeln – gelten für JEDE Session

1. **README zuerst:** Bevor du in einem Ordner arbeitest, lies dessen `README.md`.
2. **Journal-Pflicht:** Nach jedem Arbeitsschritt sofort einen Eintrag in
   `dokumentation/vorgehen.md` anhängen (Template steht dort). Append-only – bestehende
   Einträge niemals ändern oder löschen.
3. **Kleine Commits:** Nach jedem abgeschlossenen Artefakt oder Arbeitsschritt committen
   (Konventionen unten). Keine Sammel-Commits über viele Ergebnisse hinweg.
4. **Nie überschreiben:** Ergebnisse und Prompts sind versioniert (v1, v2, …). Jede Änderung
   ist eine neue Version, die alte Datei bleibt bestehen.
5. **Matrix pflegen:** Nach jeder Statusänderung einer Zelle `evaluation/ergebnismatrix.md`
   aktualisieren.
6. **Lastenhefte sind tabu:** Dateien in `lastenhefte/` niemals verändern.
7. **Original vor Korrektur:** KI-Ausgaben exakt so speichern, wie sie geliefert wurden
   (z. B. `v1.puml`). Eigene Korrekturen als separate Datei `v1-korrigiert.puml` ablegen und
   die Fehler in `notizen.md` beschreiben. Die unveränderte Original-Ausgabe ist unser
   Messobjekt – ohne sie ist die Evaluation wertlos.
8. **Nichts erfinden:** Wenn Informationen fehlen (z. B. ein Diagramm nicht vorliegt oder
   nicht lesbar ist), Zelle als offen markieren und im Journal notieren – niemals
   Evaluationsergebnisse oder Diagramminhalte erfinden.
9. **Sprache:** Alle Inhalte auf Deutsch. Dateinamen: nur Kleinbuchstaben, keine Umlaute
   (ae/oe/ue/ss), keine Leerzeichen (Bindestriche verwenden).

## Repo-Struktur

| Pfad | Zweck |
|---|---|
| `lastenhefte/` | Quellmaterial (nur lesen, nie ändern) |
| `prompts/<typ>/vN.md` | zentrale, versionierte Prompt-Bibliothek |
| `ergebnisse/<system>/<ki>/<typ>/` | generierte Artefakte + Einzelbewertung (36 Zellen) |
| `evaluation/` | Kriterien, Ergebnismatrix, Quervergleiche |
| `dokumentation/` | Vorgehens-Journal (append-only) + Reflexion |
| `praesentation/` | Folien & Demo-Material für den 20.07. |
| `templates/` | Vorlagen für Evaluationen und Prompts |

## Feste Bezeichner (exakt so schreiben, nie abwandeln)

- system: `easyride` · `easyscoot` · `easylib`
- ki: `claude` · `chatgpt` · `gemini`
- typ: `klassendiagramm` · `use-case` · `aktivitaet` · `sequenz`

Zellpfad immer: `ergebnisse/<system>/<ki>/<typ>/`

## Definition of Done – eine Zelle der Matrix

- [ ] `vN.puml` – PlantUML-Code, unverändert wie von der KI geliefert
- [ ] `vN-plantuml.png` (oder `.svg`) – daraus gerendertes Diagramm
- [ ] `vN-direkt.png` – direkt von der KI generiertes Diagrammbild
- [ ] ggf. `vN-korrigiert.puml` – falls Korrekturen zum Rendern nötig waren (Fehler in `notizen.md`)
- [ ] `evaluation.md` ausgefüllt (Vorlage: `templates/evaluation-template.md`)
- [ ] `notizen.md` – Roh-Beobachtungen aus der Generierung
- [ ] Journal-Eintrag in `dokumentation/vorgehen.md`
- [ ] `evaluation/ergebnismatrix.md` aktualisiert
- [ ] Commit

## Git-Konventionen

- Branch: nur `main`. Kein Force-Push, keine History-Umschreibung.
- Commit-Format: `bereich(zelle): beschreibung` – Beispiele:
  - `ergebnis(easyride/claude): klassendiagramm v1 + evaluation`
  - `prompt(sequenz): v2 – methodennamen explizit gefordert`
  - `eval: ki-vergleich ergaenzt`
  - `doku: journal 09.07.`
  - `praesentation: foliengeruest`
- Prompt-Iterationen und daraus folgende neue Ergebnisse als getrennte Commits – der
  Verbesserungsprozess muss in der Historie sichtbar sein.

## Methodik-Hinweise

- **Frische Session pro Generierung:** Jeder Prompt-Durchlauf bei einer KI in einer neuen,
  leeren Chat-Session – kein Kontext-Bleed zwischen Systemen, Typen oder Versionen.
- **Gleicher Prompt überall:** Pro Diagrammtyp gilt eine Prompt-Version identisch für alle
  3 KIs und alle 3 Systeme (nur das Lastenheft wird ausgetauscht). Abweichungen unbedingt
  in `notizen.md` dokumentieren, sonst ist der Vergleich nicht belastbar.
- **Rendering:** Verwendetes PlantUML-Tooling (Version/Weg) in `notizen.md` festhalten.

## Typischer Auftrag (Beispiel)

> „Lies AGENTS.md. Hier ist die Ausgabe von Gemini für das Use-Case-Diagramm zu EasyLib
> (Prompt v1): …. Lege alles ab und evaluiere."

Vorgehen: READMEs der betroffenen Ordner lesen → Dateien nach Namensschema in
`ergebnisse/easylib/gemini/use-case/` ablegen → PlantUML rendern (Korrekturen dokumentieren) →
`evaluation.md` anhand `evaluation/kriterien.md` ausfüllen → Matrix aktualisieren →
Journal-Eintrag → Commit(s).
