# prompts/ – Zentrale Prompt-Bibliothek

Ein Prompt pro Diagrammtyp **und Lastenheft/System**, versioniert. Dieselbe Prompt-Version
wird identisch für alle 3 KIs verwendet – nur so ist der KI-Vergleich belastbar. Die
Systembeschreibung (Inhalt des Lastenhefts in eigenen Worten) ist Bestandteil des Prompts.

## Struktur

```
prompts/<typ>/<system>-v1.md, <system>-v2.md, …
(typ: klassendiagramm | use-case | aktivitaet | sequenz · system: easyride | easyscoot | easylib)
```

## Aufbau jeder Datei

Zwei Schritte, beide in derselben frischen Chat-Session:

1. **Basis-Prompt** – Rolle, Konversationsregeln und Systembeschreibung in eigenen Worten
   (ersetzt den früheren `{LASTENHEFT}`-Platzhalter; Begründung der Paraphrase in
   `dokumentation/quelle-ki-prompts-oose1.md`, Abschnitt 2.2). Antwort der KI abwarten
   (Verständnis-Check).
2. **Diagramm-Prompt** – die typspezifische Aufgabe.

## Regeln

1. **Freigegebene Versionen werden nie mehr editiert.** Verbesserung = neue Datei
   `<system>-vN+1.md` mit Changelog und Begründung (die Prompt-Iteration ist Teil der
   Aufgabenstellung!).
2. Jeder Prompt fordert **beide Ausgaben** an: (a) direkt gezeichnetes Diagramm (Bild) und
   (b) PlantUML-Code. Falls eine KI das nicht in einem Durchlauf kann: in zwei Teilprompts
   in derselben frischen Session ausführen und das in `notizen.md` der Zelle dokumentieren.
3. Mindestanforderungen aus der Aufgabenstellung müssen im Prompt abgedeckt sein:
   Use-Case-Diagramm ≥ 5 Use Cases, Aktivitätsdiagramm ≥ 5 Aktivitäten,
   Sequenzdiagramm ≥ 5 Methodenaufrufe.
4. **Frische Chat-Session pro Durchlauf** (kein Kontext aus früheren Generierungen; die
   zwei Schritte einer Datei gehören zu EINEM Durchlauf).
5. Welche Prompt-Version für ein Ergebnis verwendet wurde, steht in der `evaluation.md`
   der Zelle und in der `ergebnismatrix.md`.

Herkunft der Prompts: `dokumentation/quelle-ki-prompts-oose1.md` (OOSE-I-Sammlung mit
ausführlichen Begründungen je Prompt).
