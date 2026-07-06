# Projektarbeit: Modellierung mit KI – Multi-Case-Study mit UML

Modul Informationsinfrastrukturen · FHDW · Q3-2026 · Prof. Dr. Jil Klünder
Bearbeitung: 07.–19.07.2026 · Präsentation: 20.07.2026

**Gruppe:** _TODO: Mitglieder eintragen_

## Was hier passiert

Wir generieren aus den Lastenheften von **EasyRide, EasyScoot und EasyLib** mit drei KIs
(**Claude, ChatGPT, Gemini**) je vier UML-Diagrammtypen (Klassen-, Use-Case-, Aktivitäts-,
Sequenzdiagramm) – jeweils als direkt generiertes Diagramm **und** als PlantUML-Code, den wir
rendern. Alle 36 Zellen (3 Systeme × 3 KIs × 4 Typen) werden einheitlich evaluiert und
anschließend systematisch verglichen.

## Wegweiser (insb. für Korrektoren)

| Was | Wo |
|---|---|
| Vorgehensdokumentation (chronologisch) | `dokumentation/vorgehen.md` |
| Reflexion (was ging gut / schlecht) | `dokumentation/reflexion.md` |
| Statusübersicht aller 36 Zellen | `evaluation/ergebnismatrix.md` |
| Evaluationskriterien | `evaluation/kriterien.md` |
| Quervergleiche (KIs, Systeme, PlantUML vs. direkt, …) | `evaluation/vergleiche/` |
| Verwendete Prompts (versioniert) | `prompts/` |
| Alle generierten Artefakte + Einzelbewertungen | `ergebnisse/<system>/<ki>/<typ>/` |
| Präsentation | `praesentation/` |

## Arbeiten mit KI-Agenten

Dieses Repo ist für die Zusammenarbeit mit KI-Agenten optimiert:

- `AGENTS.md` enthält die verbindlichen Regeln (wird von ChatGPT/Codex- und Gemini-Tools
  automatisch gelesen; `CLAUDE.md`/`GEMINI.md` verweisen darauf).
- Jeder Ordner hat ein eigenes `README.md` mit lokalen Regeln und Namenskonventionen.
- Typischer Einstieg in einer neuen Session: Repo einbinden und beauftragen, z. B.
  _„Lies AGENTS.md. Lege folgende ChatGPT-Ausgabe für easyride/klassendiagramm ab und evaluiere."_

Doku, Versionierung und Commits passieren dann nach den Repo-Regeln automatisch.

## Offene Punkte

- [ ] `lastenhefte/easylib.md` besorgen (fehlt noch, siehe `lastenhefte/README.md`)
- [ ] Prof. Klünder + Jochen zum Repo einladen (Abgabe erfolgt über Git)
- [ ] Besprechungstermin (09./13./14./15.07.) in Teams-Excel eintragen
- [ ] PlantUML-Rendering-Weg festlegen (einheitlich, siehe `ergebnisse/README.md`)

#Test 