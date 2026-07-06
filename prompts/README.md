# prompts/ – Zentrale Prompt-Bibliothek

Ein Prompt pro Diagrammtyp, versioniert. **Dieselbe Prompt-Version wird identisch für alle
3 KIs und alle 3 Systeme verwendet** – nur das Lastenheft wird ausgetauscht. Nur so sind die
Vergleiche belastbar.

## Struktur

```
prompts/<typ>/v1.md, v2.md, …    (typ: klassendiagramm | use-case | aktivitaet | sequenz)
```

## Regeln

1. Neue Prompts nach Vorlage `templates/prompt-template.md` anlegen.
2. **Freigegebene Versionen werden nie mehr editiert.** Verbesserung = neue Datei `vN+1.md`
   mit Changelog und Begründung (die Prompt-Iteration ist Teil der Aufgabenstellung!).
3. Der Prompt enthält den Platzhalter `{LASTENHEFT}` – beim Einsatz wird dort das
   vollständige Lastenheft eingesetzt.
4. Jeder Prompt fordert **beide Ausgaben** an: (a) direkt gezeichnetes Diagramm (Bild) und
   (b) PlantUML-Code. Falls eine KI das nicht in einem Durchlauf kann: in zwei Teilprompts
   in derselben frischen Session ausführen und das in `notizen.md` der Zelle dokumentieren.
5. Mindestanforderungen aus der Aufgabenstellung müssen im Prompt abgedeckt sein:
   Use-Case-Diagramm ≥ 5 Use Cases, Aktivitätsdiagramm ≥ 5 Aktivitäten,
   Sequenzdiagramm ≥ 5 Methodenaufrufe.
6. **Frische Chat-Session pro Durchlauf** (kein Kontext aus früheren Generierungen).
7. Welche Prompt-Version für ein Ergebnis verwendet wurde, steht in der `evaluation.md`
   der Zelle und in der `ergebnismatrix.md`.
