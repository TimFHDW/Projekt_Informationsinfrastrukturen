# Ergebnismatrix

Zentrale Statusuebersicht aller 36 Zellen (3 Systeme x 3 KIs x 4 Diagrammtypen).
**Nach jeder Statusaenderung einer Zelle aktualisieren!** Scores erst nach ausgefuellter evaluation.md eintragen (Skalen: siehe kriterien.md).

Status-Werte: `offen` -> `generiert` -> `evaluiert` -> ggf. `iteration` (neue Prompt-Version laeuft)

Notation Scores: `PU` = PlantUML-Rendering, `direkt` = direkt gezeichnetes KI-Bild. Stand 2026-07-14: 16 der 24 `v1.puml` sind gerendert und bewertet (K1/K4-PlantUML eingetragen) – **alle 16 kompilieren fehlerfrei (K1-PU=5)**. `PU offen` = Render fehlt/fehlgeschlagen: easyride/chatgpt/aktivitaet (kein Bild) sowie alle easylib-Zellen ausser claude/sequenz (Datei `v1-PlantUML.png`, 0 Byte – Gross-/Kleinschreibung + leerer Render, bitte als `v1-plantuml.png` neu rendern). Bei `claude` sind PlantUML und Direktbild dasselbe Modell (Bild aus `v1.puml` abgeleitet) – K2/K3 gelten fuer beide Formen. Gemini-Spalte: keine Artefakte -> `offen`.

| System | KI | Diagrammtyp | Status | Prompt | K1 Syntax | K2 Inhalt | K3 Vollst. | K4 Lesbarkeit |
|---|---|---|---|---|---|---|---|---|
| easyride | claude | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | 5 | 4 | PU 3 / direkt 4 |
| easyride | claude | use-case | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 5 / direkt 5 |
| easyride | claude | aktivitaet | evaluiert | v1 | PU 5 / direkt 5 | 5 | 5 | PU 5 / direkt 5 |
| easyride | claude | sequenz | evaluiert | v1 | PU 5 / direkt 5 | 4 | 5 | PU 4 / direkt 4 |
| easyride | chatgpt | klassendiagramm | evaluiert | v1 | PU 5 / direkt 5 | PU 5 / direkt 2 | PU 5 / direkt 3 | PU 4 / direkt 5 |
| easyride | chatgpt | use-case | evaluiert | v1 | PU 5 / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 | PU 4 / direkt 5 |
| easyride | chatgpt | aktivitaet | evaluiert | v1 | PU offen (Render fehlt) / direkt 3 | PU 5 / direkt 5 | PU 5 / direkt 4 | PU offen / direkt 5 |
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
| easylib | claude | klassendiagramm | evaluiert | v1 | PU offen (0-Byte-Render) / direkt 5 | 4 | 4 | PU offen / direkt 4 |
| easylib | claude | use-case | evaluiert | v1 | PU offen (0-Byte-Render) / direkt 5 | 5 | 5 | PU offen / direkt 4 |
| easylib | claude | aktivitaet | evaluiert | v1 | PU offen (0-Byte-Render) / direkt 5 | 5 | 5 | PU offen / direkt 5 |
| easylib | claude | sequenz | evaluiert | v1 | PU 5 / direkt 5 | 4 | 5 | PU 4 / direkt 4 |
| easylib | chatgpt | klassendiagramm | evaluiert | v1 | PU offen (0-Byte-Render) / direkt 5 | PU 5 / direkt 4 | PU 5 / direkt 4 | PU offen / direkt 5 |
| easylib | chatgpt | use-case | evaluiert | v1 | PU offen (0-Byte-Render) / direkt 3 | PU 5 / direkt 3 | PU 5 / direkt 3 | PU offen / direkt 3 |
| easylib | chatgpt | aktivitaet | evaluiert | v1 | PU offen (0-Byte-Render) / direkt 3 | PU 5 / direkt 4 | PU 5 / direkt 3 | PU offen / direkt 5 |
| easylib | chatgpt | sequenz | evaluiert | v1 | PU offen (0-Byte-Render) / direkt 4 | PU 5 / direkt 5 | PU 5 / direkt 5 | PU offen / direkt 5 |
| easylib | gemini | klassendiagramm | offen | – | – | – | – | – |
| easylib | gemini | use-case | offen | – | – | – | – | – |
| easylib | gemini | aktivitaet | offen | – | – | – | – | – |
| easylib | gemini | sequenz | offen | – | – | – | – | – |

## Kernbefunde (2026-07-14)

- **K1 (Syntax/Kompilierbarkeit):** Alle 16 gerenderten `v1.puml` kompilieren fehlerfrei ohne Korrektur (K1-PU=5). Damit ist die syntaktische Korrektheit fuer beide KIs bestaetigt.
- **PlantUML vs. direkt (ChatGPT):** Der PlantUML-Code ist inhaltlich durchweg korrekt (K2-PU=5); die *direkten* Bilder fallen teils stark ab – Extremfall `easyride/chatgpt/klassendiagramm` (direkt K2=2: Fahrzeug an Routenhalt statt Route, Routenhalt an Verbindung statt Haltepunkt, Buchung–Fahrgast fehlt). Der gerenderte PlantUML-Code zeigt genau diese Beziehungen korrekt. Fazit: Bei ChatGPT ist der Code deutlich zuverlaessiger als das selbstgezeichnete Bild.
- **Zeichenqualitaet (K4):** ChatGPT-Renders sind sehr sauber (meist 5), inkl. `loop`-Fragment im EasyRide-Sequenzdiagramm. Claude-Renders sind gut (4–5), Ausnahme die Klassendiagramme mit weit ausufernden Auto-Layout-Boegen (easyride 3, easyscoot 4). Beim Direktbild ist es umgekehrt: Claudes handgezeichnete Klassendiagramme sind kompakter (K4-direkt 4) als ihr PlantUML-Auto-Layout.

## Offene Punkte

- **Gemini (12 Zellen):** keine Artefakte – bleibt `offen`, nicht bewertbar (Regel 8).
- **8 fehlende/fehlerhafte Renders:** `easyride/chatgpt/aktivitaet` (kein Bild) und die 7 `easylib`-Zellen ausser `claude/sequenz` (`v1-PlantUML.png`, 0 Byte). Bitte als `v1-plantuml.png` (klein) neu rendern; danach K1/K4-PlantUML analog nachtragen. Alle 8 `v1.puml` haben die statische Struktur-Pruefung bestanden.
- **claude-Scores sind Selbstbewertungen** (dieselbe KI hat generiert) – unabhaengige Gegenpruefung empfohlen. ChatGPT-Zellen wurden von Codex bewertet; PlantUML-Seite hier ergaenzt.
