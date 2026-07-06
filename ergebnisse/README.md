# ergebnisse/ – Generierte Artefakte (36 Zellen)

Eine „Zelle" = eine Kombination aus System × KI × Diagrammtyp:

```
ergebnisse/<system>/<ki>/<typ>/
system: easyride | easyscoot | easylib
ki:     claude | chatgpt | gemini
typ:    klassendiagramm | use-case | aktivitaet | sequenz
```

Die Ordner existieren bereits – **keine neuen Ordner oder abweichende Schreibweisen anlegen.**

## Dateien pro Zelle

| Datei | Inhalt |
|---|---|
| `vN.puml` | PlantUML-Code, **exakt wie von der KI geliefert** (nicht anfassen!) |
| `vN-korrigiert.puml` | nur falls nötig: minimal korrigierte Fassung zum Rendern |
| `vN-plantuml.png` / `.svg` | aus dem (ggf. korrigierten) Code gerendertes Diagramm |
| `vN-direkt.png` | das von der KI direkt generierte Diagrammbild |
| `evaluation.md` | Einzelbewertung nach `templates/evaluation-template.md` |
| `notizen.md` | Roh-Beobachtungen: Datum, Session, Auffälligkeiten, Korrekturen, Tooling |

`N` = Nummer der verwendeten Prompt-Version (v1 = Prompt v1). Alte Versionen bleiben liegen.

## Workflow pro Zelle (Definition of Done: siehe AGENTS.md)

1. Prompt-Version aus `prompts/<typ>/` nehmen, Lastenheft einsetzen
2. In **frischer** Session der Ziel-KI ausführen
3. Beide Ausgaben unverändert speichern (`vN.puml`, `vN-direkt.png`)
4. PlantUML rendern; nötige Korrekturen → `vN-korrigiert.puml` + Beschreibung in `notizen.md`
5. `evaluation.md` anhand `evaluation/kriterien.md` ausfüllen
6. `evaluation/ergebnismatrix.md` aktualisieren
7. Journal-Eintrag in `dokumentation/vorgehen.md`
8. Commit: `ergebnis(<system>/<ki>): <typ> vN + evaluation`

## Rendering

Einheitlichen Weg verwenden und in `notizen.md` nennen (z. B. plantuml.jar lokal,
IntelliJ-PlantUML-Plugin oder plantuml.com-Server). Renderfehler sind ein
**Evaluationsergebnis** (K1), kein Ärgernis – dokumentieren statt stillschweigend fixen.
