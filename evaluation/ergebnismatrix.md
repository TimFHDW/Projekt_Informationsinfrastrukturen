# Ergebnismatrix

Zentrale Statusuebersicht aller 36 Zellen (3 Systeme x 3 KIs x 4 Diagrammtypen).
**Nach jeder Statusaenderung einer Zelle aktualisieren!** Scores erst nach ausgefuellter evaluation.md eintragen (Skalen: siehe kriterien.md).

Status-Werte: `offen` -> `generiert` -> `evaluiert` -> ggf. `iteration` (neue Prompt-Version laeuft)

Notation Scores: `PU` = PlantUML-Rendering, `direkt` = direkt gezeichnetes KI-Bild. `PU offen` = PlantUML in dieser Umgebung nicht renderbar (2026-07-14: npm/Maven/CDN gesperrt) – K1 (kompiliert?) und K4-PlantUML lokal nachrendern (z. B. IntelliJ-PlantUML-Plugin). Alle 24 vorhandenen `v1.puml` haben die statische Struktur-Pruefung bestanden (`@startuml/@enduml` paarig, Klammern balanciert, nicht abgeschnitten). Gemini-Spalte: keine Artefakte -> `offen`.

| System | KI | Diagrammtyp | Status | Prompt | K1 Syntax | K2 Inhalt | K3 Vollst. | K4 Lesbarkeit |
|---|---|---|---|---|---|---|---|---|
| easyride | claude | klassendiagramm | evaluiert | v1 | PU offen / direkt ok | 5 | 4 | PU offen / direkt 4 |
| easyride | claude | use-case | evaluiert | v1 | PU offen / direkt ok | 5 | 5 | PU offen / direkt 5 |
| easyride | claude | aktivitaet | evaluiert | v1 | PU offen / direkt ok | 5 | 5 | PU offen / direkt 5 |
| easyride | claude | sequenz | evaluiert | v1 | 5 | 4 | 5 | PU 4 / direkt 4 |
| easyride | chatgpt | klassendiagramm | evaluiert | v1 | PU offen / direkt 5 | PU 5 / direkt 2 | PU 5 / direkt 3 | PU offen / direkt 5 |
| easyride | chatgpt | use-case | evaluiert | v1 | PU offen / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 | PU offen / direkt 5 |
| easyride | chatgpt | aktivitaet | evaluiert | v1 | PU offen / direkt 3 | PU 5 / direkt 5 | PU 5 / direkt 4 | PU offen / direkt 5 |
| easyride | chatgpt | sequenz | evaluiert | v1 | PU offen / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 5 | PU offen / direkt 5 |
| easyride | gemini | klassendiagramm | offen | – | – | – | – | – |
| easyride | gemini | use-case | offen | – | – | – | – | – |
| easyride | gemini | aktivitaet | offen | – | – | – | – | – |
| easyride | gemini | sequenz | offen | – | – | – | – | – |
| easyscoot | claude | klassendiagramm | evaluiert | v1 | PU offen / direkt ok | 5 | 4 | PU offen / direkt 4 |
| easyscoot | claude | use-case | evaluiert | v1 | PU offen / direkt ok | 5 | 5 | PU offen / direkt 4 |
| easyscoot | claude | aktivitaet | evaluiert | v1 | PU offen / direkt ok | 5 | 5 | PU offen / direkt 5 |
| easyscoot | claude | sequenz | evaluiert | v1 | 5 | 4 | 5 | PU 4 / direkt 4 |
| easyscoot | chatgpt | klassendiagramm | evaluiert | v1 | PU offen / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 4 | PU offen / direkt 5 |
| easyscoot | chatgpt | use-case | evaluiert | v1 | PU offen / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU offen / direkt 3 |
| easyscoot | chatgpt | aktivitaet | evaluiert | v1 | PU offen / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU offen / direkt 5 |
| easyscoot | chatgpt | sequenz | evaluiert | v1 | PU offen / direkt 4 | PU 5 / direkt 4 | PU 5 / direkt 5 | PU offen / direkt 5 |
| easyscoot | gemini | klassendiagramm | offen | – | – | – | – | – |
| easyscoot | gemini | use-case | offen | – | – | – | – | – |
| easyscoot | gemini | aktivitaet | offen | – | – | – | – | – |
| easyscoot | gemini | sequenz | offen | – | – | – | – | – |
| easylib | claude | klassendiagramm | evaluiert | v1 | PU offen / direkt ok | 4 | 4 | PU offen / direkt 4 |
| easylib | claude | use-case | evaluiert | v1 | PU offen / direkt ok | 5 | 5 | PU offen / direkt 4 |
| easylib | claude | aktivitaet | evaluiert | v1 | PU offen / direkt ok | 5 | 5 | PU offen / direkt 5 |
| easylib | claude | sequenz | evaluiert | v1 | 5 | 4 | 5 | PU 4 / direkt 4 |
| easylib | chatgpt | klassendiagramm | evaluiert | v1 | PU offen / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 4 | PU offen / direkt 5 |
| easylib | chatgpt | use-case | evaluiert | v1 | PU offen / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU offen / direkt 3 |
| easylib | chatgpt | aktivitaet | evaluiert | v1 | PU offen / direkt 3 | PU 5 / direkt 4 | PU 5 / direkt 3 | PU offen / direkt 5 |
| easylib | chatgpt | sequenz | evaluiert | v1 | PU offen / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 | PU offen / direkt 5 |
| easylib | gemini | klassendiagramm | offen | – | – | – | – | – |
| easylib | gemini | use-case | offen | – | – | – | – | – |
| easylib | gemini | aktivitaet | offen | – | – | – | – | – |
| easylib | gemini | sequenz | offen | – | – | – | – | – |

## Offene Punkte

- **Gemini (12 Zellen):** keine Artefakte vorhanden – bleibt `offen`, kann nicht bewertet werden (Regel 8).
- **K1 (Kompilierbarkeit) + K4-PlantUML (24 Zellen):** PlantUML-Rendering in der Cowork-Umgebung am 2026-07-14 blockiert (npm 403, Maven/GitHub/CDN nicht erreichbar). Statische Struktur-Pruefung aller 24 `v1.puml` bestanden; endgueltige Kompilier-/Layout-Bewertung im Team-Renderweg (lokal) nachtragen. Ausnahme: die 3 `claude/sequenz`-Zellen wurden bereits gerendert (K1=5, K4-PlantUML=4).
- **claude-Zellen:** K2/K3/K1-direkt/K4-direkt sind Selbstbewertungen (dieselbe KI, die generiert hat); unabhaengige Gegenpruefung empfohlen. Bei claude sind PlantUML und direktes Bild dasselbe Modell (Bild aus `v1.puml` abgeleitet) – K2/K3 gelten daher fuer beide Formen.
