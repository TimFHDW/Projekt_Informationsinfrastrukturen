# Vorgehensdokumentation (Journal)

Chronologisches, append-only Journal aller Arbeitsschritte. Template und Regeln:
siehe `README.md` in diesem Ordner.

---

## 2026-07-06 | 14:15 | Claude (im Auftrag von Lewin)
Schritt: Repo-Design erarbeitet und Grundstruktur angelegt: Ordnerstruktur (36 Ergebnis-Zellen),
AGENTS.md/CLAUDE.md/GEMINI.md, alle Ordner-READMEs, Templates (Evaluation, Prompt),
Evaluationskriterien K1–K4, Ergebnismatrix, Lastenhefte EasyRide + EasyScoot übernommen.
Ergebnis: gesamte Repo-Grundstruktur (siehe Commits vom 06.07.)
Beobachtung: Lastenheft EasyLib fehlt noch (muss aus Teams/OOSE-1 besorgt werden).
Design-Entscheidung: AGENTS.md statt „Mreadme.md" als Master-Anweisungsdatei, da sie von
gängigen KI-Tools automatisch gelesen wird; Original-KI-Ausgaben werden unverändert
gespeichert, Korrekturen separat (Messobjekt-Prinzip).

## 2026-07-06 | 17:35 | Claude (im Auftrag von Linus)
Schritt: Hochgeladene Prompt-Sammlung „KI-Prompts-EasyScoot-EasyRide-EasyLib.md" (aus OOSE-I
Q3 2025, mit ausführlichen Begründungen) gesichtet und als Quelle archiviert.
Ergebnis: dokumentation/quelle-ki-prompts-oose1.md
Beobachtung: Sammlung ist systemspezifisch aufgebaut (3 Basis-Prompts mit Systembeschreibung
+ 12 Diagramm-Prompts, als zusammenhängende Konversation, nur PlantUML) und widerspricht
damit der Repo-Methodik (prompts/README.md: ein generischer Prompt je Typ, {LASTENHEFT},
frische Session, Bild + PlantUML). Entscheidung mit Linus: an Repo-Format anpassen,
Original als Quelle erhalten.

## 2026-07-06 | 17:45 | Claude (im Auftrag von Linus)
Schritt: Generische v1-Prompts je Diagrammtyp aus der Quelle destilliert. Übernommen:
Rollenzuweisung, Leitplanken gegen Hinzudichten/Weglassen, fette Mindestzahlen,
Selbstprüfungs-Checklisten, deutsche Bezeichner, Annahmen-Offenlegung. Neu gegenüber der
Quelle: {LASTENHEFT}-Platzhalter, Bild + PlantUML in einem Durchlauf, Einzel-Session statt
Konversation, Szenariowahl per Heuristik statt fester Vorgabe.
Ergebnis: prompts/klassendiagramm/v1.md, prompts/use-case/v1.md, prompts/aktivitaet/v1.md,
prompts/sequenz/v1.md (Status jeweils: entwurf)
Beobachtung: Zwei methodische Konsequenzen für die Reflexion vorgemerkt: (1) Konsistenz
zwischen Diagrammen desselben Systems ist per frischer Session nicht erzwingbar, nur
nachträglich evaluierbar; (2) freie Szenariowahl bei Aktivität/Sequenz kann zwischen
KIs/Durchläufen streuen – ggf. Kandidat für v2 mit festem Szenario. Lastenheft easylib
fehlt weiterhin; die Quelle enthält nur eine Paraphrase (kein Ersatz, Regel 8 AGENTS.md).

## 2026-07-06 | 17:55 | Claude (im Auftrag von Linus)
Schritt: Quelle und v1-Prompts einzeln committet: d2b2b3e (quelle), 84d32d3
(klassendiagramm), d4208f3 (use-case), 5b5844d (aktivitaet), bc3f12a (sequenz).
Ergebnis: 5 Commits auf main; Journal-Commit folgt separat.
Beobachtung: Git-Zwischenfall beim ersten Commit-Versuch (verkettete Commits): Auf dem
Sync-Laufwerk der Arbeitsumgebung waren Löschoperationen gesperrt, Git konnte Lock-/
Temp-Dateien nicht entfernen – Folge: korrupter Index, zurückgebliebene index.lock/HEAD.lock.
Behoben durch Freigabe der Lösch-Berechtigung, Entfernen der Locks und Index-Neuaufbau
(git reset); Objektdatenbank und Historie blieben unbeschädigt, kein Datenverlust.
Lehre für kommende Sessions: Git-Operationen auf dem Sync-Laufwerk einzeln und mit kurzen
Pausen ausführen, Zustand nach jedem Commit prüfen.
