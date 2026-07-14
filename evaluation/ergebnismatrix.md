# Ergebnismatrix

Zentrale Statusuebersicht aller 36 Zellen (3 Systeme x 3 KIs x 4 Diagrammtypen).
**Nach jeder Statusaenderung einer Zelle aktualisieren!** Scores erst nach ausgefuellter evaluation.md eintragen (Skalen: siehe kriterien.md).

Status-Werte: `offen` -> `generiert` -> `evaluiert` -> ggf. `iteration` (neue Prompt-Version laeuft)

Notation Scores: `PU` = PlantUML-Rendering, `direkt` = direkt gezeichnetes KI-Bild. **Stand 2026-07-14: alle 24 vorhandenen `v1.puml` (claude + chatgpt) sind gerendert und bewertet – alle kompilieren fehlerfrei (K1-PU = 5).** Bei `claude` sind PlantUML und Direktbild dasselbe Modell (Bild aus `v1.puml` abgeleitet) – K2/K3 gelten fuer beide Formen und stehen daher als eine Zahl. Gemini-Spalte: keine Artefakte -> `offen`.

| System | KI | Diagrammtyp | Status | Prompt | K1 Syntax | K2 Inhalt | K3 Vollst. | K4 Lesbarkeit |
|---|---|---|---|---|---|---|---|---|
| easyride | claude | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | 5 | 4 | PU 3 / direkt 4 |
| easyride | claude | use-case | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 5 / direkt 5 |
| easyride | claude | aktivitaet | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 5 / direkt 5 |
| easyride | claude | sequenz | evaluiert | v1 | PU 5 / direkt 5 | 4 | 5 | PU 4 / direkt 4 |
| easyride | chatgpt | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | PU 5 / direkt 2 | PU 5 / direkt 3 | PU 4 / direkt 5 |
| easyride | chatgpt | use-case | evaluiert | v1 | PU 5 / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 | PU 4 / direkt 5 |
| easyride | chatgpt | aktivitaet | evaluiert | v1 | PU 5 / direkt 3 | PU 5 / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 5 |
| easyride | chatgpt | sequenz | evaluiert | v1 | PU 5 / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 |
| easyride | gemini | klassendiagramm | offen | – | – | – | – | – |
| easyride | gemini | use-case | offen | – | – | – | – | – |
| easyride | gemini | aktivitaet | offen | – | – | – | – | – |
| easyride | gemini | sequenz | offen | – | – | – | – | – |
| easyscoot | claude | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | 5 | 4 | PU 4 / direkt 4 |
| easyscoot | claude | use-case | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 4 / direkt 4 |
| easyscoot | claude | aktivitaet | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 5 / direkt 5 |
| easyscoot | claude | sequenz | evaluiert | v1 | PU 5 / direkt 5 | 4 | 5 | PU 4 / direkt 4 |
| easyscoot | chatgpt | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 4 | PU 5 / direkt 5 |
| easyscoot | chatgpt | use-case | evaluiert | v1 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU 4 / direkt 3 |
| easyscoot | chatgpt | aktivitaet | evaluiert | v1 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 5 |
| easyscoot | chatgpt | sequenz | evaluiert | v1 | PU 5 / direkt 4 | PU 5 / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 |
| easyscoot | gemini | klassendiagramm | offen | – | – | – | – | – |
| easyscoot | gemini | use-case | offen | – | – | – | – | – |
| easyscoot | gemini | aktivitaet | offen | – | – | – | – | – |
| easyscoot | gemini | sequenz | offen | – | – | – | – | – |
| easylib | claude | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | 4 | 4 | PU 4 / direkt 4 |
| easylib | claude | use-case | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 4 / direkt 4 |
| easylib | claude | aktivitaet | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 5 / direkt 5 |
| easylib | claude | sequenz | evaluiert | v1 | PU 5 / direkt 5 | 4 | 5 | PU 4 / direkt 4 |
| easylib | chatgpt | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 4 | PU 5 / direkt 5 |
| easylib | chatgpt | use-case | evaluiert | v1 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU 3 / direkt 3 |
| easylib | chatgpt | aktivitaet | evaluiert | v1 | PU 5 / direkt 3 | PU 5 / direkt 4 | PU 5 / direkt 3 | PU 5 / direkt 5 |
| easylib | chatgpt | sequenz | evaluiert | v1 | PU 5 / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 | PU 5 / direkt 5 |
| easylib | gemini | klassendiagramm | offen | – | – | – | – | – |
| easylib | gemini | use-case | offen | – | – | – | – | – |
| easylib | gemini | aktivitaet | offen | – | – | – | – | – |
| easylib | gemini | sequenz | offen | – | – | – | – | – |

## Kernbefunde (2026-07-14)

- **K1 (Syntax/Kompilierbarkeit):** Alle 24 `v1.puml` kompilieren fehlerfrei ohne Korrektur (K1-PU = 5) – fuer beide KIs, alle vier Diagrammtypen. Syntaktische Korrektheit vollstaendig bestaetigt.
- **PlantUML vs. direkt – Kernbefund (ChatGPT):** Der PlantUML-Code ist inhaltlich durchweg korrekt (K2-PU = 5); die *direkt gezeichneten* Bilder fallen teils deutlich ab. Extremfall `easyride/chatgpt/klassendiagramm` (direkt K2 = 2: Fahrzeug an Routenhalt statt Route, Routenhalt an Verbindung statt Haltepunkt, Buchung–Fahrgast fehlt) – der gerenderte Code zeigt genau diese Beziehungen korrekt. Fazit: Bei ChatGPT ist der Code deutlich zuverlaessiger als das selbstgezeichnete Bild.
- **PlantUML vs. direkt (Claude):** Direktbild wurde aus dem `v1.puml` abgeleitet -> inhaltlich identisch; der Vergleich ist nur bei der Zeichenqualitaet (K4) aussagekraeftig. Ausnahme: die unabhaengig erzeugten Sequenzdiagramme (auch inhaltlich vergleichbar).
- **K4 (Zeichenqualitaet):** ChatGPT-Renders sind sehr sauber (meist 5, inkl. `loop`-Fragment und `create`/`extend`-Notation). Claude-Renders 4–5, Ausnahme die **Klassendiagramme mit ausufernden Auto-Layout-Boegen** (easyride 3, easyscoot/easylib 4). Umgekehrt sind Claudes *handgezeichnete* Klassendiagramme kompakter (K4-direkt 4) als ihr eigenes PlantUML-Auto-Layout. Schwaechstes Render-Layout: `easylib/chatgpt/use-case` (K4 3, viele Kreuzungen).
- **Systeme:** Grosse Direktbild-Schwaechen v. a. bei ChatGPTs EasyScoot-/EasyLib-Use-Case-/Aktivitaetsdiagrammen (direkt teils 3); Klassendiagramme und Sequenzdiagramme durchweg stark.

## Offene Punkte

- **Gemini (12 Zellen):** keine Artefakte – bleibt `offen`, nicht bewertbar (Regel 8).
- **claude-Scores sind Selbstbewertungen** (dieselbe KI hat generiert) – unabhaengige Gegenpruefung empfohlen. ChatGPT-Zellen wurden von Codex bewertet; die PlantUML-Seite (K1/K4-PU) ist hier ergaenzt.
- **Propagierung in die einzelnen `evaluation.md`:** Die K1/K4-PlantUML-Scores stehen bisher nur in dieser Matrix; in den 24 `evaluation.md` sind die K1/K4-PU-Zeilen teils noch als „offen/ausstehend" markiert (Folgeschritt).
