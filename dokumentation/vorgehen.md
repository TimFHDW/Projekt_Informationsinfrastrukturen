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

## 2026-07-06 | 18:20 | Claude (im Auftrag von Linus)
Schritt: Prompt-Bibliothek auf Wunsch von Linus umgestellt: statt eines generischen Prompts
je Typ jetzt je Typ-Ordner drei systemspezifische Dateien (easyscoot/easyride/easylib-v1.md),
Inhalt jeweils Basis-Prompt (mit Systembeschreibung) + Diagramm-Prompt im Original-Wortlaut
der Quelle. Einzige inhaltliche Änderung: beide Ausgabeformen (direktes Bild + PlantUML)
werden gefordert, sonst wären die DoD-Artefakte vN-direkt.png nicht erzeugbar. Generische
v1.md entfernt (bleiben über Git-Historie nachvollziehbar), prompts/README.md an die neue
Struktur angepasst.
Ergebnis: 12 Dateien prompts/<typ>/<system>-v1.md; prompts/README.md aktualisiert;
generische prompts/<typ>/v1.md entfernt
Beobachtung: templates/prompt-template.md passt nicht mehr zur neuen Struktur
(Metadaten-Tabelle, {LASTENHEFT}-Platzhalter) – Anpassung noch offen. Methodik: Die zwei
Schritte einer Datei (Basis + Diagramm) laufen in EINER frischen Session; Regel „frische
Session pro Generierung" (AGENTS.md) bleibt gewahrt, solange je Typ-Durchlauf eine neue
Session genutzt wird.

## 2026-07-06 | 20:10 | Claude (im Auftrag von Tim)
Schritt: Klassendiagramm fuer die Zelle easylib/claude/klassendiagramm als PlantUML generiert
(Quelle: Systembeschreibung in prompts/klassendiagramm/easylib-v1.md, da kein
lastenhefte/easylib.md existiert). Vorschlag vorab von Tim freigegeben. DoD-Dateien der Zelle
angelegt und Matrix-Zelle auf „generiert" (Prompt v1) gesetzt.
Ergebnis: ergebnisse/easylib/claude/klassendiagramm/{v1.puml, notizen.md, evaluation.md};
evaluation/ergebnismatrix.md aktualisiert
Beobachtung: Abweichungen von der Methodik dokumentiert (siehe notizen.md): (1) Generierung in
laufender Cowork-Session statt frischer, isolierter Chat-Session – moeglicher Kontext-Einfluss;
(2) nur PlantUML-Form erzeugt, geforderte „direkt"-Bildform (v1-direkt.png) fehlt noch;
(3) Rendering (K1) und Lesbarkeit (K4) nicht bewertet, da in dieser Umgebung kein PlantUML-
Rendering moeglich war. K2/K3 nur vorlaeufig selbstbewertet gegen die Paraphrase (kein
offizielles Lastenheft easylib). Noch offen: Reproduktion in frischer Session, v1-direkt.png,
Rendering + finale Evaluation, Commit. Nebenbefund: Nutzer verwies auf „lastenheft/easyride.md"
als Quelle – das ist jedoch das EasyRide-Lastenheft; fuer EasyLib bleibt die Paraphrase im
Prompt die einzige Quelle.

## 2026-07-06 | 20:25 | Claude (im Auftrag von Tim)
Schritt: Offizielles EasyLib-Lastenheft aus den hochgeladenen Vorlesungsfolien
(2025-Q3-OOSE-I-Kapitel 4, Folien 24–27 = Seite 180–183) transkribiert und als
lastenhefte/easylib.md angelegt (Stil wie easyride.md/easyscoot.md). Damit ist die zuvor im
Journal notierte Luecke geschlossen. Anschliessend v1.puml der Zelle
easylib/claude/klassendiagramm gegen das nun offizielle Lastenheft geprueft.
Ergebnis: lastenhefte/easylib.md (neu); evaluation.md und notizen.md der Zelle aktualisiert
(Quellbezug jetzt lastenhefte/easylib.md, K2 auf 4 praezisiert).
Beobachtung: Diagramm inhaltlich deckungsgleich mit dem Lastenheft – keine Korrektur an
v1.puml noetig, Original bleibt unveraendert (Regel 7). Zwei dokumentierte Nuancen: (a)
Leihfrist-Verlaengerung bewusst gegen den woertlichen (unplausiblen) Text modelliert; (b)
Ausleihe/Reservierung auf Exemplar-/Medium-Ebene statt streng „Buchexemplar"/„Buch". Prompt-
Paraphrase stichprobenartig gegen das Original geprueft: inhaltlich konsistent, kein v2 noetig.

## 2026-07-06 | 20:45 | Claude (im Auftrag von Tim)
Schritt: Analog zur EasyLib-Zelle die Klassendiagramme fuer easyride/claude/klassendiagramm und
easyscoot/claude/klassendiagramm als PlantUML generiert (gemaess Schritt-2-Vorgaben der Prompts
prompts/klassendiagramm/easyride-v1.md bzw. easyscoot-v1.md; Referenz-Lastenhefte
lastenhefte/easyride.md und lastenhefte/easyscoot.md). Je Zelle DoD-Dateien angelegt und
Matrix-Zellen auf „generiert" (Prompt v1) gesetzt.
Ergebnis: ergebnisse/easyride/claude/klassendiagramm/{v1.puml, notizen.md, evaluation.md};
ergebnisse/easyscoot/claude/klassendiagramm/{v1.puml, notizen.md, evaluation.md};
evaluation/ergebnismatrix.md aktualisiert
Beobachtung: EasyRide mit eigener Routenhalt-Klasse ({ordered}), ungerichteter Verbindung
(Multiplizitaet 2) sowie Kapazitaets- und Zentrale-Regel als Constraints. EasyScoot mit
Nutzer-Oberklasse, drei Status-Enums und Rechnungssystem als «external system». Gleiche
Methodik-Abweichungen wie bei EasyLib dokumentiert (keine frische Session; nur PlantUML, keine
v1-direkt.png; kein Rendering, daher K1/K4 offen; K2/K3 vorlaeufige Selbstbewertung gegen die
offiziellen Lastenhefte). Noch offen je Zelle: frische Session, v1-direkt.png, Rendering +
finale Evaluation, Commit.

## 2026-07-06 | 21:10 | Claude (im Auftrag von Lewin)
Schritt: Aktivitaetsdiagramm fuer die Zelle easylib/claude/aktivitaet als PlantUML generiert
(Prompt: prompts/aktivitaet/easylib-v1.md, Szenario „Bibliothekar pflegt ein neues
Buchexemplar ein"; Referenz: lastenhefte/easylib.md). Entwurf vorab von Lewin freigegeben,
KI-Ausgabe dabei unveraendert. DoD-Dateien der Zelle angelegt, Matrix-Zelle auf
„generiert" (v1) gesetzt.
Ergebnis: ergebnisse/easylib/claude/aktivitaet/{v1.puml, notizen.md, evaluation.md};
evaluation/ergebnismatrix.md aktualisiert
Beobachtung: Gleiche Methodik-Abweichungen wie bei den Klassendiagramm-Zellen (laufende
Cowork-Session statt frischer Session – diesmal zusaetzlich mit Vorkontext des bereits
generierten EasyLib-Klassendiagramms derselben KI, moeglicher Kontext-Einfluss; nur
PlantUML-Form, v1-direkt.png fehlt; kein Rendering moeglich: plantuml.jar-Download erneut
blockiert, HTTP 403 vom Proxy bei Maven Central – K1/K4 offen). K2/K3 vorlaeufig
selbstbewertet (je 5). Commit auf Wunsch von Lewin nicht durch den Agenten; steht aus.

## 2026-07-06 | 21:25 | Claude (im Auftrag von Lewin)
Schritt: Aktivitaetsdiagramm fuer die Zelle easyride/claude/aktivitaet als PlantUML generiert
(Prompt: prompts/aktivitaet/easyride-v1.md, Szenario „Kunde bucht eine Fahrt"; Referenz:
lastenhefte/easyride.md). Entwurf vorab von Lewin freigegeben, KI-Ausgabe dabei unveraendert.
DoD-Dateien der Zelle angelegt, Matrix-Zelle auf „generiert" (v1) gesetzt.
Ergebnis: ergebnisse/easyride/claude/aktivitaet/{v1.puml, notizen.md, evaluation.md};
evaluation/ergebnismatrix.md aktualisiert
Beobachtung: Fachregeln im Diagramm verankert (Kapazitaetspruefung vor Routenerweiterung;
Zentrale als Beginn/Ende neuer Routen); „Neue Route anlegen" als duplizierter Knoten in
beiden Nein-Zweigen (PlantUML ohne goto). Methodik-Abweichungen wie zuvor, zusaetzlich:
unmittelbar zuvor wurde in derselben Session das easylib-Aktivitaetsdiagramm erzeugt ->
moeglicher Struktur-Uebertrag zwischen Systemen (gleicher Diagrammtyp). Nur PlantUML-Form,
v1-direkt.png fehlt; kein Rendering moeglich (plantuml.jar-Download blockiert), K1/K4 offen;
K2/K3 vorlaeufig selbstbewertet (je 5). Commit macht Lewin selbst.

## 2026-07-06 | 21:37 | Claude (im Auftrag von Lewin)
Schritt: Aktivitaetsdiagramm fuer die Zelle easyscoot/claude/aktivitaet als PlantUML generiert
(Prompt: prompts/aktivitaet/easyscoot-v1.md, Szenario „E-Scooter ausleihen und nutzen";
Referenz: lastenhefte/easyscoot.md). Entwurf vorab von Lewin freigegeben, KI-Ausgabe dabei
unveraendert. DoD-Dateien der Zelle angelegt, Matrix-Zelle auf „generiert" (v1) gesetzt.
Damit liegen alle drei Aktivitaetsdiagramme der Claude-Spalte vor.
Ergebnis: ergebnisse/easyscoot/claude/aktivitaet/{v1.puml, notizen.md, evaluation.md};
evaluation/ergebnismatrix.md aktualisiert
Beobachtung: Preisberechnung wie gefordert in der Rechnungssystem-Swimlane; genau eine
Entscheidung (Mindestvorgabe) mit Nein-Zweig in eigenem Endknoten; Leihstatus „in Benutzung"
als systemseitige Wirkung der Buchung. Methodik-Abweichungen wie zuvor, verschaerft:
drittes Aktivitaetsdiagramm in derselben Session -> moeglicher Struktur-Uebertrag zwischen
den Systemen. Nur PlantUML-Form, v1-direkt.png fehlt; kein Rendering moeglich (plantuml.jar-
Download blockiert), K1/K4 offen; K2/K3 vorlaeufig selbstbewertet (je 5). Commit macht
Lewin selbst.
