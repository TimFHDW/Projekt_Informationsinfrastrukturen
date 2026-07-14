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

## 2026-07-06 | 22:03 | Claude (im Auftrag von Basti)
Schritt: Sequenzdiagramm easylib/claude v1 generiert (Prompt `prompts/sequenz/easylib-v1.md`,
Szenario „Bibliothekar verleiht ein Buchexemplar an einen Kunden"), Entwurf vor Ablage von
Basti freigegeben. Danach in der Cowork-Sandbox gerendert: plantuml.jar 1.2019.06 aus dem
npm-Paket node-plantuml (direkte Downloads/apt in der Sandbox blockiert, npm funktioniert);
`v1.puml` kompilierte ohne Korrektur.
Ergebnis: ergebnisse/easylib/claude/sequenz/ (v1.puml, v1-plantuml.png, notizen.md,
evaluation.md); evaluation/ergebnismatrix.md: Zelle auf generiert/v1.
Beobachtung: Methodik-Abweichungen wie beim Klassendiagramm (laufende Cowork-Session mit
Vorkontext statt frischer Session, Zweischritt-Prompt nicht getrennt ausgefuehrt,
v1-direkt.png fehlt) in notizen.md dokumentiert. Annahme Leihfrist 28 Tage (Lastenheft nennt
keine Dauer). K1=5/K2=4/K3=5/K4-PlantUML=4 als vorlaeufige Selbstbewertung; unabhaengige
Pruefung durch Teammitglied und Rendern mit einheitlichem Team-Renderweg stehen aus.

## 2026-07-06 | 22:30 | Claude (im Auftrag von Basti)
Schritt: Sequenzdiagramme easyride/claude v1 („Fahrer bestaetigt Erreichen eines
Haltepunkts") und easyscoot/claude v1 („Kunde beendet Nutzung eines E-Scooters") generiert
(Prompts `prompts/sequenz/easyride-v1.md` / `easyscoot-v1.md`), Entwuerfe vor Ablage von
Basti freigegeben; beide in der Cowork-Sandbox gerendert (plantuml.jar 1.2019.06 aus npm
node-plantuml) – beide kompilierten ohne Korrektur.
Ergebnis: ergebnisse/easyride/claude/sequenz/ und ergebnisse/easyscoot/claude/sequenz/
(je v1.puml, v1-plantuml.png, notizen.md, evaluation.md); Matrix: beide Zellen generiert/v1.
Beobachtung: Gleiche Methodik-Abweichungen wie bei easylib (laufende Session, kein
Zweischritt-Prompt, v1-direkt.png fehlt); zusaetzlich Typ-interner Kontext-Bleed moeglich,
da alle drei Sequenz-Zellen in einer Sitzung entstanden (aehnliche Fassaden-Struktur).
easyscoot: Signaturkonflikt Prompt-Beispiel vs. Klassendiagramm bei berechnePreis –
zugunsten der Konsistenzregel entschieden (berechnePreis(fahrt)). Vorlaeufige
Selbstbewertung je K1=5/K2=4/K3=5/K4-PlantUML=4; unabhaengige Pruefung ausstehend.

## 2026-07-06 | 22:40 | Claude (im Auftrag von Basti)
Schritt: Git-/Sync-Zwischenfall behoben: Nach dem easyscoot-Commit war der Index korrupt
(bad signature); zudem hatte die Sync-Verzoegerung dazu gefuehrt, dass (a) der Commit 3323a80
einen veralteten Matrix-Stand erfasste (easyscoot-Zeile noch „offen") und (b) die
Arbeitskopien von ergebnismatrix.md und den easylib-Sequenz-Dateien abgeschnitten auf der
Platte lagen (Dateiende mitten in der Zeile, defektes UTF-8-Byte). Parallel dazu existiert
ein manueller IntelliJ-Commit bf32283 („Sequenzdiagramm") mit den vollstaendigen
easylib-Dateien.
Ergebnis: Index neu aufgebaut (rm .git/index + git reset); easylib-Dateien aus HEAD
wiederhergestellt; ergebnismatrix.md aus HEAD wiederhergestellt, easyscoot-Zeile erneut auf
generiert/v1 gesetzt und defekte Schlusszeile repariert (36 Zeilen verifiziert). Alle sechs
committeten easyride-/easyscoot-Zelldateien gegen HEAD geprueft: intakt.
Beobachtung: Bestaetigt die Lehre vom Nachmittag - Git-Operationen auf dem Sync-Laufwerk
einzeln ausfuehren und Zustand nach jedem Commit pruefen; zusaetzlich neu: nach jedem
Datei-Schreibvorgang kurz warten, bevor git add laeuft (Sync-Latenz), und Arbeitskopien
nach Commits stichprobenartig auf Truncation pruefen. Commit-Konvention: bf32283 folgt
nicht dem Schema `bereich(zelle): beschreibung` - fuer die Historien-Bewertung im Team
ansprechen, nicht umschreiben (Regel: keine History-Umschreibung).

## 2026-07-07 | 18:45 | Claude (im Auftrag von Linus)
Schritt: Fehlende „direkt"-Bildform der drei Klassendiagramm-Zellen der Claude-Spalte
nachgeliefert. Je Zelle das Klassendiagramm von der KI direkt als Bild gezeichnet (eigenes
Python/Pillow-Zeichenskript der KI, Layout/Koordinaten von der KI bestimmt, KEINE
PlantUML-Beteiligung), inhaltsgleich zum jeweils abgelegten v1.puml (Prompt-Regel: beide
Ausgabeformen muessen uebereinstimmen). Alle drei PNGs visuell verifiziert; zwei
Layout-Korrekturen vor Ablage (easyride: Kantenfuehrung „zugeteilt" kreuzte Notiz;
easylib: Kantenfuehrung „umfasst" und Label „betrifft").
Ergebnis: ergebnisse/easyride/claude/klassendiagramm/v1-direkt-easyride.png;
ergebnisse/easyscoot/claude/klassendiagramm/v1-direkt-easyscoot.png;
ergebnisse/easylib/claude/klassendiagramm/v1-direkt-easylib.png; notizen.md (Nachtrag +
DoD-Checkliste) und evaluation.md (K1-direkt, K3-Artefaktebene, K4-direkt je Score 4
vorlaeufig, Abschnitt PlantUML vs. direkt) der drei Zellen aktualisiert.
Beobachtung: (1) Namensabweichung von AGENTS.md (vN-direkt.png) auf ausdruecklichen Wunsch
von Linus: Dateinamen mit Systemnamen (v1-direkt-<system>.png); Zellpfad unveraendert.
(2) Methodik: Bilder nachtraeglich aus v1.puml abgeleitet statt im selben
Generierungsdurchlauf – inhaltliche Uebereinstimmung PlantUML vs. direkt damit
konstruktionsbedingt, fuer vergleiche/plantuml-vs-direkt.md nur K4 (Zeichenqualitaet)
verwertbar; zudem alle drei Bilder in einer Cowork-Session (Struktur-Uebertrag moeglich,
keine frische Session). (3) ergebnismatrix.md unveraendert (Status bleibt „generiert",
keine Statusaenderung). (4) Erneut Sync-Latenz beobachtet: Zeichenskript kam in der Sandbox
abgeschnitten an, Ausfuehrung ueber /tmp-Kopie; PNGs nach Ablage per Integritaetspruefung
(PIL verify) bestaetigt. Commits macht Linus selbst.

## 2026-07-07 | 15:52 | Claude (im Auftrag von Tim)
Schritt: Die drei „direkt gezeichneten" Aktivitaetsdiagramme (Szenarien gemaess
prompts/aktivitaet/*-v1.md) als SVG in Cowork erzeugt, von Tim visuell freigegeben und via
librsvg-2 + cairo (ctypes; plantuml.jar/pip in dieser Umgebung blockiert) zu PNG gerendert und
als v1-direkt.png in die drei Aktivitaets-Zellen gelegt (Ablageort mit Tim geklaert: DoD-Zellen,
nicht prompts/aktivitaet/).
Ergebnis: ergebnisse/{easyride,easyscoot,easylib}/claude/aktivitaet/v1-direkt.png (je 1360px,
2x); je Zelle notizen.md (Checkbox) und evaluation.md (K1/K4 Direktbild) aktualisiert.
Beobachtung: Die Bilder zeigen dieselben Szenarien wie die vorhandenen v1.puml, sind aber in
einzelnen Labels/Schritten leicht verdichtet (z. B. EasyRide ohne separaten Schritt „Buchung
starten/bestaetigen"; EasyScoot Rechnungs-Uebermittlung als Abhaengigkeitspfeil; EasyLib
[ja]-Zweig direkt zu „Exemplar anlegen"). Fuer strikte 1:1-Deckung beide Formen in einer
frischen Session neu erzeugen. Der Direktbild-Weg nutzt librsvg (nicht PlantUML); fuer die noch
fehlenden v1-plantuml.png der Aktivitaets-Zellen steht laut Journal 22:03 der node-plantuml-Weg
(npm) bereit.

## 2026-07-07 | 17:30 | Claude (im Auftrag von Lewin)
Schritt: Fehlende „direkt"-Bildform der drei Use-Case-Zellen der Claude-Spalte nachgeliefert
(Auftrag: Prompts aus prompts/use-case/*-v1.md ausfuehren und die Direktbilder in den
DoD-Zellen ablegen). Je Zelle das Use-Case-Diagramm von der KI direkt als Bild gezeichnet
(eigenes Python/Pillow-Zeichenskript der KI, Layout/Koordinaten von der KI bestimmt, KEINE
PlantUML-Beteiligung), inhaltsgleich zum jeweils abgelegten v1.puml (Prompt-Regel: beide
Ausgabeformen muessen uebereinstimmen). Alle drei PNGs visuell verifiziert und per
MD5-Vergleich + PIL-verify auf Integritaet geprueft (Sync-Latenz-Lektion vom 06./07.07.).
Ergebnis: ergebnisse/easyride/claude/use-case/v1-direkt-easyride.png;
ergebnisse/easyscoot/claude/use-case/v1-direkt-easyscoot.png;
ergebnisse/easylib/claude/use-case/v1-direkt-easylib.png; je Zelle notizen.md (Nachtrag +
DoD-Checkliste) und evaluation.md (K1-direkt, K3-Artefaktebene, K4-direkt, Abschnitt
PlantUML vs. direkt) aktualisiert; evaluation/ergebnismatrix.md: die drei
use-case/claude-Zeilen von „offen" auf „generiert" (v1) gesetzt – diese Aktualisierung
stand seit dem 06.07. aus (offener DoD-Punkt der drei Zellen).
Beobachtung: (1) Namensabweichung von AGENTS.md (vN-direkt.png) auf Wunsch von Lewin:
Dateinamen mit Systemnamen (v1-direkt-<system>.png), analog zu den Klassendiagramm-Zellen.
(2) Methodik wie beim Klassendiagramm-Nachtrag vom 07.07.: Bilder nachtraeglich aus v1.puml
abgeleitet statt im selben Generierungsdurchlauf -> Uebereinstimmung PlantUML vs. direkt
konstruktionsbedingt, fuer vergleiche/plantuml-vs-direkt.md nur K4 verwertbar; alle drei
Bilder in einer Cowork-Session (Struktur-Uebertrag moeglich: identisches Spaltenlayout).
(3) K4-Selbstbewertung direkt (vorlaeufig): easyride 5 (keine Kreuzungen), easyscoot 4
(Kreuzung der Sekundaerakteur-Kanten), easylib 4 (Kreuzungen durch geteilte Use Cases,
kurzer extend-Pfeil). Commits macht Lewin selbst.

## 2026-07-08 | 12:09 | Claude (im Auftrag von Tim)
Schritt: Fehlende „direkt"-Bildform der drei Sequenz-Zellen der Claude-Spalte nachgeliefert
(Prompts aus prompts/sequenz/*-v1.md). WICHTIGER UNTERSCHIED zu den Klassendiagramm-/Use-Case-
Nachtraegen (07.07.): Auf ausdrueckliche Anweisung von Tim wurden die zugehoerigen v1.puml
BEWUSST NICHT angesehen; jedes Sequenzbild ist eine UNABHAENGIGE Generierung allein aus dem
Prompt (Schritt-1-Systembeschreibung + Schritt-2-Szenario). Damit ist der Vergleich PlantUML
vs. direkt hier auch inhaltlich (nicht nur K4) belastbar. Bilder von der KI direkt gezeichnet
ueber einen eigenen Sequenzdiagramm-Generator (Python) -> SVG -> PNG via librsvg-2 + cairo
(ctypes); KEINE PlantUML-Beteiligung. easylib und easyride visuell verifiziert.
Ergebnis: ergebnisse/easyride/claude/sequenz/v1-direkt-easyride.png;
ergebnisse/easyscoot/claude/sequenz/v1-direkt-easyscoot.png;
ergebnisse/easylib/claude/sequenz/v1-direkt-easylib.png; je Zelle notizen.md (Nachtrag +
DoD-Checkliste) und evaluation.md (Datum, K1-direkt, K4-direkt) aktualisiert.
Beobachtung: (1) Namensabweichung von AGENTS.md (vN-direkt.png) auf Wunsch von Tim: Dateinamen
mit Systemnamen (v1-direkt-<system>.png), analog zu den anderen Direktbild-Nachtraegen.
(2) Szenarien: easyride „Fahrer bestaetigt Erreichen eines Haltepunkts" (6 Aufrufe); easyscoot
„Kunde beendet Nutzung" (5 Aufrufe, Preis in der Rechnungssystem-Lebenslinie); easylib
„Bibliothekar verleiht Buchexemplar" (6 Aufrufe inkl. «create» der Ausleihe). Alle mit
synchronen Aufrufen + Antwortpfeilen, >= 5 Methodenaufrufe. (3) Methodik-Abweichungen: keine
frische Session, Zweischritt-Prompt nicht getrennt, alle drei Bilder in einer Session.
(4) K4-direkt vorlaeufig je 4 (einzelne lange Methodensignaturen ragen in enge Nachbar-Spalten).
ergebnismatrix.md: Sequenz-Zellen stehen bereits auf „generiert" (v1), keine Statusaenderung.
(5) Umgebungshinweis: Der bash-Mount der Sandbox zeigte vorgehen.md veraltet (68 Zeilen) –
Abgleich/Anhaengen daher ueber die Datei-Tools (aktueller Workspace-Stand).

## 2026-07-10 | 14:33 | ChatGPT (im Auftrag von Tim)

Schritt: Die drei systemspezifischen Aktivitaetsdiagramm-Prompts fuer EasyRide, EasyScoot und
EasyLib aus `prompts/aktivitaet/*-v1.md` sowie die zugehoerigen Projektanweisungen aus den
hochgeladenen README- und AGENTS-Dateien gelesen. Anschliessend auf Wunsch von Tim zunaechst
ausschliesslich die direkt generierten Diagrammbilder erstellt; die PlantUML-Ausgaben sollen
zu einem spaeteren Zeitpunkt separat erzeugt werden. Der erste Generierungsdurchlauf lieferte
alle drei Aktivitaetsdiagramme gemeinsam in einer Gesamtgrafik. Diese wurden anschliessend
zwar technisch in drei einzelne PNG-Dateien getrennt, auf Wunsch von Tim jedoch nochmals als
vollstaendig eigenstaendige Diagrammgrafiken neu generiert. Dabei entstanden zunaechst
EasyRide und EasyScoot separat. EasyLib wurde beim ersten Nachgenerierungsversuch
versehentlich erneut gemeinsam mit EasyScoot ausgegeben und deshalb anschliessend nochmals
allein als eigenstaendige Grafik erzeugt.

Ergebnis: Drei separat generierte Aktivitaetsdiagramme als PNG fuer die Szenarien
`easyride`: „Kunde bucht eine Fahrt",
`easyscoot`: „E-Scooter ausleihen und nutzen" und
`easylib`: „Bibliothekar pflegt ein neues Buchexemplar ein".
Die PlantUML-Codes und daraus gerenderten PlantUML-Bilder wurden in diesem Arbeitsschritt
bewusst noch nicht erstellt.

Beobachtung: Der Generierungsablauf wich von der in `AGENTS.md` und den Prompt-Dateien
vorgesehenen Methodik ab, da alle drei Systeme in derselben laufenden Chat-Session bearbeitet
wurden und damit ein moeglicher Kontext- bzw. Struktur-Uebertrag zwischen den Diagrammen
besteht. Zusaetzlich wurden die in den Prompt-Dateien vorgesehenen zwei Schritte
(Basis-Prompt mit Verstaendnis-Check und anschliessender Diagramm-Prompt) nicht als getrennte
Nachrichten mit dazwischenliegender Bestaetigung ausgefuehrt. Der erste Durchlauf erzeugte
eine gemeinsame Gesamtgrafik statt drei separater Einzelbilder; diese Darstellung wurde
verworfen und die Diagramme danach einzeln neu generiert. Beim EasyLib-Nachtrag trat erneut
eine fehlerhafte gemeinsame Ausgabe mit EasyScoot auf, weshalb EasyLib nochmals separat
erzeugt wurde. Fuer die spaetere Evaluation muss ausserdem geprueft werden, ob jede finale
Direktgrafik alle formalen Mindestanforderungen des jeweiligen Prompts vollstaendig erfuellt,
insbesondere die geforderten Entscheidungen, beschrifteten Kanten und Swimlanes. Die
Direktbilder wurden unabhaengig von PlantUML erzeugt; ein spaeterer Vergleich zwischen
Direktbild und PlantUML-Ausgabe bleibt damit grundsaetzlich moeglich.

## 2026-07-11 | 14:18 | Codex (im Auftrag von Tim)
Schritt: Das direkt generierte ChatGPT-Aktivitaetsdiagramm v1 fuer EasyRide visuell gegen
`lastenhefte/easyride.md`, `prompts/aktivitaet/easyride-v1.md` und die Kriterien K1–K4
geprueft. Fehlende Begleitdateien angelegt und die Ergebnismatrix aktualisiert.
Ergebnis: `ergebnisse/easyride/chatgpt/aktivitaet/evaluation.md` und `notizen.md` neu;
`evaluation/ergebnismatrix.md` fuer easyride/chatgpt/aktivitaet auf `generiert` (v1) gesetzt.
Beobachtung: Nur das Direktbild liegt vor; PlantUML-Code und Rendering bleiben offen. Das
Bild erfuellt die Aktivitaets-Mindestzahl und bildet den Kernablauf korrekt ab, enthaelt aber
nur eine statt der geforderten zwei Entscheidungen. Die Direktbild-Scores sind deshalb
vorlaeufig und in der Matrix explizit als solche gekennzeichnet.

## 2026-07-11 | 14:22 | Codex (im Auftrag von Tim)
Schritt: Das direkt generierte ChatGPT-Aktivitaetsdiagramm v1 fuer EasyScoot visuell gegen
`lastenhefte/easyscoot.md`, `prompts/aktivitaet/easyscoot-v1.md` und die Kriterien K1–K4
geprueft. Fehlende Begleitdateien angelegt und die Ergebnismatrix aktualisiert.
Ergebnis: `ergebnisse/easyscoot/chatgpt/aktivitaet/evaluation.md` und `notizen.md` neu;
`evaluation/ergebnismatrix.md` fuer easyscoot/chatgpt/aktivitaet auf `generiert` (v1) gesetzt.
Beobachtung: Nur das Direktbild liegt vor; PlantUML-Code und Rendering bleiben offen. Die
Aktivitaets-Mindestzahl und alle Kernaktivitaeten sind enthalten, aber die geforderte
Entscheidung fehlt. Ausserdem wird die Preisberechnung vor Erfassung der Nutzungsdaten
angestossen und „Nutzung beenden“ der System- statt der Kundenlane zugeordnet.

## 2026-07-11 | 14:24 | Codex (im Auftrag von Tim)
Schritt: Das direkt generierte ChatGPT-Aktivitaetsdiagramm v1 fuer EasyLib visuell gegen
`lastenhefte/easylib.md`, `prompts/aktivitaet/easylib-v1.md` und die Kriterien K1–K4
geprueft. Fehlende Begleitdateien angelegt und die Ergebnismatrix aktualisiert.
Ergebnis: `ergebnisse/easylib/chatgpt/aktivitaet/evaluation.md` und `notizen.md` neu;
`evaluation/ergebnismatrix.md` fuer easylib/chatgpt/aktivitaet auf `generiert` (v1) gesetzt.
Beobachtung: Nur das Direktbild liegt vor; PlantUML-Code und Rendering bleiben offen. Beide
Entscheidungen, die Mindestaktivitaeten sowie die Trennung von Werk und Exemplar sind
enthalten. Statt der geforderten drei Swimlanes existiert jedoch nur die Lane Bibliothekar.
Ein vorgeschriebener Git-Commit war nicht moeglich, weil der Schreibzugriff auf den
Git-Index nicht freigegeben wurde; die Aenderungen bleiben deshalb uncommitted.

## 2026-07-11 | 14:35 | Codex (im Auftrag von Tim)
Schritt: `prompts/klassendiagramm/easyride-v1.md` als strukturierte Bildspezifikation in
einem eigenstaendigen Built-in-Imagegen-Durchlauf ausgefuehrt, das Original-PNG unveraendert
als `ergebnisse/easyride/chatgpt/klassendiagramm/v1-direkt-chatgpt.png` abgelegt, visuell
gegen Lastenheft und Kriterien geprueft sowie Evaluation, Notizen und Matrix aktualisiert.
Ergebnis: Direktbild, `evaluation.md`, `notizen.md`; Matrixstatus `generiert`, Prompt v1.
Beobachtung: Das Bild ist sehr gut lesbar, ordnet aber Fahrzeug dem Routenhalt und den
Routenhalt der Verbindung statt den fachlich richtigen Klassen Route bzw. Haltepunkt zu;
ausserdem fehlt Buchung–Fahrgast. PlantUML-Code und -Rendering bleiben offen.

## 2026-07-11 | 14:36 | Codex (im Auftrag von Tim)
Schritt: `prompts/klassendiagramm/easyscoot-v1.md` in einem frischen, eigenstaendigen
Built-in-Imagegen-Durchlauf ausgefuehrt, das Original-PNG unveraendert als
`ergebnisse/easyscoot/chatgpt/klassendiagramm/v1-direkt-chatgpt.png` abgelegt, visuell
geprueft sowie Evaluation, Notizen und Matrix aktualisiert.
Ergebnis: Direktbild, `evaluation.md`, `notizen.md`; Matrixstatus `generiert`, Prompt v1.
Beobachtung: Klassen, Attribute, Vererbung und Enumerationen sind weitgehend vollstaendig;
die Preis-Abhaengigkeit geht jedoch fachlich unpassend vom E-Scooter aus. PlantUML bleibt offen.

## 2026-07-11 | 14:37 | Codex (im Auftrag von Tim)
Schritt: `prompts/klassendiagramm/easylib-v1.md` in einem frischen, eigenstaendigen
Built-in-Imagegen-Durchlauf ausgefuehrt, das Original-PNG unveraendert als
`ergebnisse/easylib/chatgpt/klassendiagramm/v1-direkt-chatgpt.png` abgelegt, visuell
geprueft sowie Evaluation, Notizen und Matrix aktualisiert.
Ergebnis: Direktbild, `evaluation.md`, `notizen.md`; Matrixstatus `generiert`, Prompt v1.
Beobachtung: Werk-/Exemplartrennung, Vererbung, Genre und Schnittstellen sind enthalten;
die Reservierung ist nicht eindeutig mit Medium verbunden. Die vorhandene fachfremde
`Projekt_Informationsinfrastrukturen.puml` blieb gemaess Originalschutz unveraendert.

## 2026-07-13 | 10:33 | Codex (im Auftrag von Tim)
Schritt: PlantUML-Code fuer das ChatGPT-Aktivitaetsdiagramm EasyRide anhand von
`prompts/aktivitaet/easyride-v1.md` und `lastenhefte/easyride.md` erzeugt und unveraendert
als v1-Original abgelegt.
Ergebnis: `ergebnisse/easyride/chatgpt/aktivitaet/v1.puml`.
Beobachtung: Code enthaelt zwei Entscheidungen, beschriftete Kanten, beide Swimlanes,
Kapazitaetspruefung vor der Routenerweiterung sowie Start- und Endknoten. Erzeugung erfolgte
nachtraeglich zum Direktbild und in derselben Codex-Session wie die weiteren Zellen.

## 2026-07-13 | 10:34 | Codex (im Auftrag von Tim)
Schritt: PlantUML-Code fuer das ChatGPT-Aktivitaetsdiagramm EasyScoot anhand von
`prompts/aktivitaet/easyscoot-v1.md` und `lastenhefte/easyscoot.md` erzeugt und unveraendert
als v1-Original abgelegt.
Ergebnis: `ergebnisse/easyscoot/chatgpt/aktivitaet/v1.puml`.
Beobachtung: Entscheidung mit Ja-/Nein-Ausgaengen und drei Swimlanes enthalten;
Preisberechnung liegt beim Rechnungssystem. Nachtraegliche Erzeugung zum Direktbild.

## 2026-07-13 | 10:35 | Codex (im Auftrag von Tim)
Schritt: PlantUML-Code fuer das ChatGPT-Aktivitaetsdiagramm EasyLib anhand von
`prompts/aktivitaet/easylib-v1.md` und `lastenhefte/easylib.md` erzeugt und unveraendert
als v1-Original abgelegt.
Ergebnis: `ergebnisse/easylib/chatgpt/aktivitaet/v1.puml`.
Beobachtung: Zwei Entscheidungen, drei Swimlanes, Zusammenfuehrung der Alternativen sowie
Trennung von Werk und Exemplar enthalten. Die README-Angabe zum fehlenden EasyLib-Lastenheft
ist veraltet; die vorhandene Datei wurde ausschliesslich gelesen.

## 2026-07-13 | 10:36 | Codex (im Auftrag von Tim)
Schritt: PlantUML-Code fuer das ChatGPT-Klassendiagramm EasyRide anhand von
`prompts/klassendiagramm/easyride-v1.md` und `lastenhefte/easyride.md` erzeugt und
unveraendert als v1-Original abgelegt.
Ergebnis: `ergebnisse/easyride/chatgpt/klassendiagramm/v1.puml`.
Beobachtung: Geordnete Routenhalte, ungerichtete Verbindung, Multiplizitaeten, zentrale
Methoden und beide Fachregel-Notizen enthalten. Nachtraegliche Erzeugung zum Direktbild.

## 2026-07-13 | 10:37 | Codex (im Auftrag von Tim)
Schritt: PlantUML-Code fuer das ChatGPT-Klassendiagramm EasyScoot anhand von
`prompts/klassendiagramm/easyscoot-v1.md` und `lastenhefte/easyscoot.md` erzeugt und
unveraendert als v1-Original abgelegt.
Ergebnis: `ergebnisse/easyscoot/chatgpt/klassendiagramm/v1.puml`.
Beobachtung: Gemeinsame Nutzerkonto-Oberklasse, Status-Enumerationen, externe
Rechnungssystem-Schnittstelle, Attribute, Methoden und Multiplizitaeten enthalten.

## 2026-07-13 | 10:38 | Codex (im Auftrag von Tim)
Schritt: PlantUML-Code fuer das ChatGPT-Klassendiagramm EasyLib anhand von
`prompts/klassendiagramm/easylib-v1.md` und `lastenhefte/easylib.md` erzeugt und
unveraendert als v1-Original abgelegt.
Ergebnis: `ergebnisse/easylib/chatgpt/klassendiagramm/v1.puml`.
Beobachtung: Abstraktes Medium, Buch-/Hoerbuch-Vererbung, getrennte Exemplare, Autor,
Genre, Ausleihe, Reservierung und externe Schnittstellen enthalten. Die fachfremde Datei
`Projekt_Informationsinfrastrukturen.puml` blieb unveraendert bestehen.

## 2026-07-13 | 10:42 | Codex (im Auftrag von Tim)
Schritt: Fuer alle sechs neuen `v1.puml` eine statische Strukturpruefung durchgefuehrt,
SHA-256-Pruefsummen erfasst und den Versuch unternommen, den offiziellen PlantUML-Renderer
1.2026.3 fuer Kompilierung und PNG-Rendering temporaer zu laden. Danach je Zelle
`evaluation.md` und `notizen.md` sowie die Ergebnismatrix aktualisiert.
Ergebnis: Statische Pruefung aller sechs Codes unauffaellig; Bewertungen enthalten getrennte
PlantUML-/Direktbild-Befunde; `evaluation/ergebnismatrix.md` aktualisiert. Die Zellen bleiben
auf `generiert`, da `v1-plantuml.png` weiterhin fehlt.
Beobachtung: Lokal waren Java 17, aber weder PlantUML-Kommando noch JAR vorhanden. Der
Download des offiziellen JAR wurde nicht freigegeben; daher keine Kompilierung, kein
Rendering und keine erfundenen K1-/K4-PlantUML-Scores. Die Originalcodes wurden nach der
Ablage nicht veraendert; es war keine `v1-korrigiert.puml` erforderlich bzw. belegbar.

## 2026-07-14 | 10:43 | Codex (im Auftrag von Lewin)
Schritt: Root- und Bereichs-READMEs, die drei freigegebenen Use-Case-Prompts v1,
Evaluationskriterien, Vorlage, Ergebnismatrix und den Ist-Stand der drei
ChatGPT/Use-Case-Zellen geprueft.
Ergebnis: `prompts/use-case/easyride-v1.md`, `easyscoot-v1.md` und `easylib-v1.md` als
Grundlage bestaetigt; alle drei Zielzellen enthalten bislang nur `.gitkeep` und stehen in
`evaluation/ergebnismatrix.md` auf `offen`.
Beobachtung: Der Auftrag betrifft die noch fehlenden direkt generierten Diagrammbilder.
PlantUML-Code und -Rendering sind damit weiterhin offene Bestandteile der vollstaendigen DoD.

## 2026-07-14 | 10:47 | Codex (im Auftrag von Linus)
Schritt: Verbindliche Agenten-, Imagegen-, README-, Prompt- und Evaluationsregeln fuer die
drei ChatGPT-Sequenzdiagramme geprueft; Zielzellen und Git-Arbeitsbaum inventarisiert.
Ergebnis: Als Eingaben wurden `prompts/sequenz/easyride-v1.md`,
`prompts/sequenz/easyscoot-v1.md` und `prompts/sequenz/easylib-v1.md` bestaetigt; die drei
Zielzellen enthalten bislang nur `.gitkeep` und sind in der Matrix `offen`.
Beobachtung: Jeder Bilddurchlauf wird ohne Bildreferenz als eigenstaendige Generierung
ausgefuehrt. Ein erster Git-Status-Aufruf scheiterte an der Safe-Directory-Pruefung; der
erneute rein lesende Aufruf mit lokalem `safe.directory`-Parameter funktionierte. Die
unversionierte benutzerseitige Datei `.idea/vcs.xml` bleibt unberuehrt.

## 2026-07-14 | 10:48 | Codex (im Auftrag von Lewin)
Schritt: `prompts/use-case/easyride-v1.md` als strukturierte Bildspezifikation in einem
eigenstaendigen Built-in-Imagegen-Durchlauf ausgefuehrt, das unveraenderte Ergebnis in die
Zielzelle kopiert und visuell geprueft.
Ergebnis: `ergebnisse/easyride/chatgpt/use-case/v1-direkt.png`.
Beobachtung: Das Diagramm enthaelt genau die geforderten zwei Akteure und fuenf Use Cases
innerhalb der Systemgrenze. Die Assoziationslinien enden mit kleinen sichtbaren Abstaenden
vor den Akteursfiguren; dieser Notationsmangel wird in der Evaluation festgehalten.

## 2026-07-14 | 10:46 | Codex (im Auftrag von Lewin)
Schritt: Das EasyRide-Direktbild gegen `lastenhefte/easyride.md` und
`evaluation/kriterien.md` bewertet, Rohbeobachtungen dokumentiert und die Ergebnismatrix
aktualisiert.
Ergebnis: `ergebnisse/easyride/chatgpt/use-case/evaluation.md` und `notizen.md` neu;
`evaluation/ergebnismatrix.md` fuer easyride/chatgpt/use-case auf `generiert` (v1) gesetzt.
Beobachtung: K1 direkt 4/5, K2 direkt 5/5, K3 direkt 5/5, K4 direkt 5/5. PlantUML-Code
und -Rendering bleiben offen. Der Zeitstempel 10:48 im unmittelbar vorherigen Eintrag war
ein Erfassungsfehler; gemaess Append-only-Regel wurde der Eintrag nicht nachtraeglich geaendert.

## 2026-07-14 | 10:50 | Codex (im Auftrag von Linus)
Schritt: `prompts/sequenz/easyride-v1.md` als strukturierte Bildspezifikation in einem
eigenstaendigen Built-in-Imagegen-Durchlauf ohne Bildreferenz ausgefuehrt.
Ergebnis: Unveraenderte Erstausgabe unter
`C:/Users/admin/.codex/generated_images/019f5fcd-3397-7841-919a-47d84bd0624a/exec-5cdb13fd-1121-479c-b49b-901c14bef353.png`.
Beobachtung: Das Original wird als Naechstes in die DoD-Zelle kopiert und erst danach
formal sowie inhaltlich bewertet; erkannte Fehler werden nicht im Bild korrigiert.

## 2026-07-14 | 10:51 | Codex (im Auftrag von Linus)
Schritt: EasyRide-Direktbild unveraendert als
`ergebnisse/easyride/chatgpt/sequenz/v1-direkt.png` abgelegt, gegen
`lastenhefte/easyride.md` und `evaluation/kriterien.md` visuell geprueft sowie
`evaluation.md`, `notizen.md` und Ergebnismatrix aktualisiert.
Ergebnis: Zelle `easyride/chatgpt/sequenz` steht auf `generiert` mit Prompt v1 und
Direktbild-Scores K1 5, K2 4, K3 5, K4 5; PlantUML-Anteile bleiben offen.
Beobachtung: Fuenf Aufrufe samt Antworten sind sauber lesbar. Kleinere fachliche
Unschaerfen sind die ungenutzte Lebenslinie `Betroffene Fahrgaeste` und die Ermittlung des
Fahrgastwechsels vor der Bestimmung des naechsten Haltepunkts. Der erste Sammel-Patch
meldete nach bereits angewendeten Datei- und Matrix-Hunks einen Kontextkonflikt beim
Matrix-Hunk; der fehlende Journal-Hunk wurde deshalb separat append-only nachgetragen.

## 2026-07-14 | 10:51 | Codex (im Auftrag von Lewin)
Schritt: `prompts/use-case/easyscoot-v1.md` als strukturierte Bildspezifikation in einem
eigenstaendigen Built-in-Imagegen-Durchlauf ausgefuehrt, das unveraenderte Ergebnis in die
Zielzelle kopiert und visuell geprueft.
Ergebnis: `ergebnisse/easyscoot/chatgpt/use-case/v1-direkt.png`.
Beobachtung: Alle fuenf Akteure und elf geforderten Use Cases sind enthalten. Das Bild
vertauscht jedoch rechts mehrere fachliche Zuordnungen: `Nutzung beenden` fuehrt zum
E-Scooter statt zum Rechnungssystem, waehrend `Wartungsmodus beenden` zum Rechnungssystem
fuehrt. Mehrere Assoziationen enden zudem vor den Akteursfiguren.

## 2026-07-14 | 10:52 | Codex (im Auftrag von Lewin)
Schritt: Das EasyScoot-Direktbild gegen `lastenhefte/easyscoot.md` und
`evaluation/kriterien.md` bewertet, Rohbeobachtungen dokumentiert und die Ergebnismatrix
aktualisiert.
Ergebnis: `ergebnisse/easyscoot/chatgpt/use-case/evaluation.md` und `notizen.md` neu;
`evaluation/ergebnismatrix.md` fuer easyscoot/chatgpt/use-case auf `generiert` (v1) gesetzt.
Beobachtung: K1 direkt 3/5, K2 direkt 3/5, K3 direkt 3/5, K4 direkt 3/5. Ausschlaggebend
sind die falschen beziehungsweise mehrdeutigen Zuordnungen der beiden Sekundaerakteure.
PlantUML-Code und -Rendering bleiben offen.

## 2026-07-14 | 10:55 | Codex (im Auftrag von Linus)
Schritt: `prompts/sequenz/easyscoot-v1.md` als strukturierte Bildspezifikation in einem
eigenstaendigen Built-in-Imagegen-Durchlauf ohne Bildreferenz ausgefuehrt.
Ergebnis: Unveraenderte Erstausgabe unter
`C:/Users/admin/.codex/generated_images/019f5fcd-3397-7841-919a-47d84bd0624a/exec-5b21b9a5-60f3-4169-9d06-7c0856baf49b.png`.
Beobachtung: Die Ausgabe enthaelt zusaetzlich zur korrekten abschliessenden Rueckgabe eine
vorzeitige `Fahrtzusammenfassung` direkt nach der Statusaktualisierung. Dieser Fehler bleibt
im Original erhalten und wird in Evaluation und Notizen bewertet.

## 2026-07-14 | 10:56 | Codex (im Auftrag von Linus)
Schritt: EasyScoot-Direktbild unveraendert als
`ergebnisse/easyscoot/chatgpt/sequenz/v1-direkt.png` abgelegt, gegen
`lastenhefte/easyscoot.md` und `evaluation/kriterien.md` visuell geprueft sowie
`evaluation.md`, `notizen.md` und Ergebnismatrix aktualisiert.
Ergebnis: Zelle `easyscoot/chatgpt/sequenz` steht auf `generiert` mit Prompt v1 und
Direktbild-Scores K1 4, K2 4, K3 5, K4 5; PlantUML-Anteile bleiben offen.
Beobachtung: Die fachliche Kernsequenz und die externe Preisberechnung sind vollstaendig.
Der zusaetzliche vorzeitige Antwortpfeil zum Kunden ist als Originalfehler dokumentiert und
wurde nicht aus dem Bild entfernt.

## 2026-07-14 | 10:56 | Codex (im Auftrag von Lewin)
Schritt: `prompts/use-case/easylib-v1.md` als strukturierte Bildspezifikation in einem
eigenstaendigen Built-in-Imagegen-Durchlauf ausgefuehrt, das unveraenderte Ergebnis in die
Zielzelle kopiert und visuell geprueft.
Ergebnis: `ergebnisse/easylib/chatgpt/use-case/v1-direkt.png`.
Beobachtung: Das Bild enthaelt alle geforderten Akteure und Funktionsbezeichnungen sowie
eine fachlich passende `<<extend>>`-Beziehung fuer den optionalen Katalogimport. Entgegen der
Promptvorgabe wurden `Bestand durchsuchen` und `Standort und Status einsehen` jedoch jeweils
doppelt gezeichnet; die vernetzten Bibliotheken sind zudem falsch mit `Leihfrist verlaengern`
verbunden. Das Original bleibt als Messobjekt unveraendert.

## 2026-07-14 | 10:57 | Codex (im Auftrag von Lewin)
Schritt: Das EasyLib-Direktbild gegen `lastenhefte/easylib.md` und
`evaluation/kriterien.md` bewertet, Rohbeobachtungen dokumentiert und die Ergebnismatrix
aktualisiert.
Ergebnis: `ergebnisse/easylib/chatgpt/use-case/evaluation.md` und `notizen.md` neu;
`evaluation/ergebnismatrix.md` fuer easylib/chatgpt/use-case auf `generiert` (v1) gesetzt.
Beobachtung: K1 direkt 3/5, K2 direkt 3/5, K3 direkt 3/5, K4 direkt 3/5. Der optionale
Katalogimport ist korrekt als `<<extend>>` modelliert; Duplikate und falsche beziehungsweise
fehlende Akteurszuordnungen senken die Bewertung. PlantUML-Code und -Rendering bleiben offen.

## 2026-07-14 | 10:58 | Codex (im Auftrag von Lewin)
Schritt: Abschliessende Konsistenzpruefung der drei erzeugten Direktbilder, Zell-Dateien und
Matrixzeilen sowie `git diff --check` ausgefuehrt.
Ergebnis: Fuer easyride, easyscoot und easylib liegen jeweils ein lesbares PNG mit
1693 x 929 Pixeln, `evaluation.md` und `notizen.md` vor; alle drei Matrixzeilen stehen auf
`generiert` mit Prompt v1. Die Diff-Pruefung meldet keine Whitespace-Fehler.
Beobachtung: Die Bilddateien sind technisch intakt. Die vollstaendige DoD bleibt pro Zelle
offen, weil `v1.puml` und `v1-plantuml.png` beziehungsweise `.svg` nicht Teil dieses
Direktbild-Auftrags waren und weiterhin fehlen.

## 2026-07-14 | 11:00 | Codex (im Auftrag von Linus)
Schritt: `prompts/sequenz/easylib-v1.md` als strukturierte Bildspezifikation in einem
eigenstaendigen Built-in-Imagegen-Durchlauf ohne Bildreferenz ausgefuehrt.
Ergebnis: Unveraenderte Erstausgabe unter
`C:/Users/admin/.codex/generated_images/019f5fcd-3397-7841-919a-47d84bd0624a/exec-13eca668-c704-4a73-a695-f24273132582.png`.
Beobachtung: Die `create`-Nachricht ist sichtbar, die Lebenslinie `Ausleihe` beginnt jedoch
entgegen der UML-Erzeugungsnotation bereits am oberen Teilnehmerkopf. Diese Abweichung
bleibt im Original und wird formal bewertet.

## 2026-07-14 | 11:01 | Codex (im Auftrag von Linus)
Schritt: EasyLib-Direktbild unveraendert als
`ergebnisse/easylib/chatgpt/sequenz/v1-direkt.png` abgelegt, gegen
`lastenhefte/easylib.md` und `evaluation/kriterien.md` visuell geprueft sowie
`evaluation.md`, `notizen.md` und Ergebnismatrix aktualisiert.
Ergebnis: Zelle `easylib/chatgpt/sequenz` steht auf `generiert` mit Prompt v1 und
Direktbild-Scores K1 4, K2 5, K3 5, K4 5; PlantUML-Anteile bleiben offen.
Beobachtung: Inhalt, Werk-/Exemplartrennung und Mindestanzahl sind vollstaendig. Als
Originalfehler ist dokumentiert, dass die Ausleihe-Lebenslinie trotz `create`-Nachricht zu
frueh beginnt. `lastenhefte/easylib.md` ist entgegen der veralteten README-Angabe vorhanden
und wurde ausschliesslich gelesen.

## 2026-07-14 | 11:03 | Codex (im Auftrag von Linus)
Schritt: Abschlusspruefung der drei ChatGPT-Sequenz-Direktbilder, Begleitdateien,
Matrixzeilen, SHA-256-Pruefsummen, Git-Index und Commit-Historie durchgefuehrt.
Ergebnis: Alle drei `v1-direkt.png` liegen mit `evaluation.md` und `notizen.md` in den
korrekten DoD-Zellen; alle Bilder sind 1693 x 929 px, die dokumentierten Pruefsummen stimmen,
und die Matrix fuehrt die drei Zellen als `generiert` mit Prompt v1. Einzelcommits:
`e7bb458` (EasyRide), `1a7bc78` (EasyScoot), `1566c72` (EasyLib).
Beobachtung: Branch ist `main`, der Index ist sauber und der Branch liegt drei Commits vor
`origin/main`. Nur die bereits vorgefundenen unversionierte Datei `.idea/vcs.xml` bleibt
unveraendert ausserhalb des Auftrags. PlantUML-Code und -Rendering bleiben in allen drei
Zellen offen; deshalb lautet der Status korrekt `generiert` statt `evaluiert`.

## 2026-07-14 | 11:11 | Codex (im Auftrag von Linus)
Schritt: Auf ausdruecklichen Auftrag die Auftraggeberangabe in den acht von Codex neu
angelegten Journal-Eintraegen vom 14.07.2026 (10:47 bis 11:03 Uhr) von `Tim` auf `Linus`
korrigiert; alle aelteren Eintraege blieben unveraendert.
Ergebnis: `dokumentation/vorgehen.md`.
Beobachtung: Die gezielte Korrektur bestehender Ueberschriften ist eine ausdruecklich
beauftragte Ausnahme von der Append-only-Regel; dieser Nachtrag macht sie nachvollziehbar.

## 2026-07-14 | 11:19 | Codex (im Auftrag von Linus)
Schritt: `AGENTS.md` sowie die READMEs von Repository, Prompts, Ergebnissen, Evaluation,
Dokumentation und Lastenheften gelesen; die drei ChatGPT-Sequenzzellen, vorhandenen
Klassendiagramme und das lokale PlantUML-Tooling inventarisiert.
Ergebnis: In allen drei Sequenzzellen fehlen `v1.puml` und das PlantUML-Rendering; Prompt
v1, Direktbild, `evaluation.md` und `notizen.md` sind vorhanden. Java 17 ist installiert,
aber weder ein PlantUML-Kommando noch eine PlantUML-JAR ist lokal verfuegbar.
Beobachtung: Die Codes werden je System separat aus dem jeweiligen Prompt, Lastenheft und
ChatGPT-Klassendiagramm abgeleitet und unveraendert als Originalausgabe gespeichert. Eine
Kompilierung oder ein Rendering ist ohne PlantUML-Tooling nicht belegbar und bleibt offen.

## 2026-07-14 | 11:21 | Codex (im Auftrag von Linus)
Schritt: PlantUML-Code fuer das ChatGPT-Sequenzdiagramm EasyRide anhand von
`prompts/sequenz/easyride-v1.md`, `lastenhefte/easyride.md` und dem vorhandenen
ChatGPT-Klassendiagramm erzeugt und unveraendert als v1-Original abgelegt.
Ergebnis: `ergebnisse/easyride/chatgpt/sequenz/v1.puml`; SHA-256
`E8701E8CEE519DFDB4D79DF2548B06EA08051C0523BA162962BFA9AED01CE950`.
Beobachtung: Der Code enthaelt fuenf synchrone Aufrufe samt Antworten, die geforderten
Lebenslinien und die drei EasyRide-Fachinvarianten als Notiz. Neue System-, Route- und
Routenhaltoperationen sowie der zusaetzliche Parameter von `restfahrzeitBerechnen` sind im
Diagramm als gedankliche Klassendiagramm-Ergaenzungen ausgewiesen.

## 2026-07-14 | 11:22 | Codex (im Auftrag von Linus)
Schritt: EasyRide-`v1.puml` statisch auf Blockstruktur, Aufruf-/Antwortanzahl,
Aktivierungspaare, Loop und Klammern geprueft; anschließend `evaluation.md`, `notizen.md`
und Ergebnismatrix um die belegbaren PlantUML-Befunde ergaenzt.
Ergebnis: Statische Strukturpruefung ohne Auffaelligkeit; Matrixwerte K2 PlantUML 5 und K3
PlantUML 5. K1 und K4 PlantUML bleiben offen, da Kompilierung und Rendering fehlen.
Beobachtung: Inhaltlich behebt der Code die Reihenfolgeunschärfe des Direktbilds, indem er
zuerst den naechsten Routenhalt und danach dessen Fahrgastwechsel ermittelt. Ein
Layoutvergleich ist erst nach einem PlantUML-Rendering moeglich.

## 2026-07-14 | 11:24 | Codex (im Auftrag von Linus)
Schritt: PlantUML-Code fuer das ChatGPT-Sequenzdiagramm EasyScoot anhand von
`prompts/sequenz/easyscoot-v1.md`, `lastenhefte/easyscoot.md` und dem vorhandenen
ChatGPT-Klassendiagramm erzeugt und unveraendert als v1-Original abgelegt.
Ergebnis: `ergebnisse/easyscoot/chatgpt/sequenz/v1.puml`; SHA-256
`2B7B57650C4C4AA729632FBC94194C1E36EDC0293882207BA3D5B56EA2C2A47F`.
Beobachtung: Der Code enthaelt fuenf synchrone Aufrufe samt Antworten und uebernimmt
`nutzungBeenden` sowie `preisBerechnen(fahrt: Fahrt)` aus dem Klassendiagramm. Das
Fahrtobjekt transportiert die dort modellierten Werte Dauer, Kilometer und Wattstunden;
fehlende System-, Scooter- und Fahrtoperationen sind als gedankliche Ergaenzungen markiert.

## 2026-07-14 | 11:25 | Codex (im Auftrag von Linus)
Schritt: EasyScoot-`v1.puml` statisch auf Blockstruktur, Aufruf-/Antwortanzahl,
Aktivierungspaare und Klammern geprueft; anschließend `evaluation.md`, `notizen.md` und
Ergebnismatrix um die belegbaren PlantUML-Befunde ergaenzt.
Ergebnis: Statische Strukturpruefung ohne Auffaelligkeit; Matrixwerte K2 PlantUML 5 und K3
PlantUML 5. K1 und K4 PlantUML bleiben offen, da Kompilierung und Rendering fehlen.
Beobachtung: Der Code gibt die Fahrtzusammenfassung erst nach Fahrtdaten- und externer
Preisermittlung genau einmal zurueck und vermeidet damit den dokumentierten vorzeitigen
Antwortpfeil des Direktbilds. Ein Layoutvergleich bleibt bis zum Rendering offen.

## 2026-07-14 | 11:28 | Codex (im Auftrag von Linus)
Schritt: PlantUML-Code fuer das ChatGPT-Sequenzdiagramm EasyLib anhand von
`prompts/sequenz/easylib-v1.md`, `lastenhefte/easylib.md` und dem vorhandenen
ChatGPT-Klassendiagramm erzeugt und unveraendert als v1-Original abgelegt.
Ergebnis: `ergebnisse/easylib/chatgpt/sequenz/v1.puml`; SHA-256
`30C506195885FF2ADCE7E5E5BF7393B5E590A6C359B0FF9CB91CF9820261345A`.
Beobachtung: Der Code enthaelt sechs synchrone Aufrufe samt Antworten. `Exemplar` wird als
physisches Buchexemplar verwendet; `Ausleihe` wird erst an der `create`-Nachricht als
Teilnehmer erzeugt. Die Annahme zur mehrdeutigen Leihfristverlaengerung und fehlende
Klassendiagrammoperationen sind als Notizen ausgewiesen.

## 2026-07-14 | 11:29 | Codex (im Auftrag von Linus)
Schritt: EasyLib-`v1.puml` statisch auf Blockstruktur, Aufruf-/Antwortanzahl,
Aktivierungspaare, Create-Deklaration und Klammern geprueft; anschließend `evaluation.md`,
`notizen.md` und Ergebnismatrix um die belegbaren PlantUML-Befunde ergaenzt.
Ergebnis: Statische Strukturpruefung ohne Auffaelligkeit; Matrixwerte K2 PlantUML 5 und K3
PlantUML 5. K1 und K4 PlantUML bleiben offen, da Kompilierung und Rendering fehlen.
Beobachtung: Anders als im Direktbild wird `Ausleihe` im Code erst an der
`create participant`-Deklaration eingefuehrt. Damit beginnt ihre Lebenslinie am fachlich
und syntaktisch vorgesehenen Erzeugungszeitpunkt; ein Layoutvergleich bleibt offen.

## 2026-07-14 | 11:31 | Codex (im Auftrag von Linus)
Schritt: Abschlusspruefung aller drei neuen ChatGPT-Sequenz-PlantUML-Codes samt
Pruefsummen, Mindestaufrufen, Antworten, Aktivierungspaaren, Begleitdateien, Matrix,
Git-Index und Commit-Historie durchgefuehrt.
Ergebnis: EasyRide und EasyScoot enthalten je fuenf, EasyLib sechs synchrone Aufrufe; in
allen Codes stimmen Aufruf-/Antwort- und Aktivierungszahlen ueberein. Alle drei SHA-256-
Pruefsummen entsprechen den Notizen, und EasyLib verwendet `create participant` vor der
ersten Ausleihe-Verwendung. Commits: `7140c88`, `7bfc247`, `644669c`.
Beobachtung: Branch `main` liegt vier Commits vor `origin/main`; Index und Diff-Pruefungen
sind sauber. Nur die bereits vorhandene unversionierte Datei `.idea/vcs.xml` bleibt
unveraendert. Mangels lokalem PlantUML-Tooling bleiben Kompilierung, Renderdateien sowie K1
und K4 PlantUML offen; die Zellen bleiben deshalb korrekt auf Status `generiert`.

## 2026-07-14 | 11:34 | Codex (im Auftrag des Tim)
Schritt: Den Verlust von Journal-Eintraegen im Merge-Commit `392e312` untersucht und die
acht Use-Case-Eintraege aus `f3a1cb3` sowie die neun Sequenz-Eintraege aus `488587d`
wortgetreu und append-only wieder zusammengefuehrt.
Ergebnis: `dokumentation/vorgehen.md` enthaelt wieder beide Arbeitsstraenge.
Beobachtung: Beim konfliktbehafteten Merge war nur der gemeinsame Stand bis 13.07.2026
uebernommen worden. Die Ergebnisartefakte selbst waren nicht verloren. Es wurde weder die
Git-Historie umgeschrieben noch ein Push ausgefuehrt.

## 2026-07-14 | 12:12 | Codex (im Auftrag von Lewin)
Schritt: `AGENTS.md` sowie die Root- und Bereichs-READMEs gelesen und den Ist-Stand der drei
ChatGPT/Use-Case-Zellen geprueft.
Ergebnis: In easyride, easyscoot und easylib liegen Direktbild, `evaluation.md` und
`notizen.md` vor; `v1.puml` und PlantUML-Rendering fehlen jeweils noch.
Beobachtung: Fuer diesen Auftrag werden ausschliesslich die drei originalen PlantUML-Codes
nach Prompt v1 erzeugt und die betroffenen Begleitdateien aktualisiert. Auf ausdruecklichen
Wunsch von Lewin erfolgen weder Commit noch Push.

## 2026-07-14 | 12:13 | Codex (im Auftrag von Lewin)
Schritt: PlantUML-Code fuer das ChatGPT-Use-Case-Diagramm EasyRide anhand von
`prompts/use-case/easyride-v1.md` und `lastenhefte/easyride.md` erzeugt und unveraendert als
v1-Original abgelegt.
Ergebnis: `ergebnisse/easyride/chatgpt/use-case/v1.puml`.
Beobachtung: Der Code enthaelt genau die zwei geforderten Akteure, die Systemgrenze
`EasyRide` und die fuenf abschliessend genannten Use Cases. Auf unbegruendete
`include`-/`extend`-Beziehungen und interne Routenplanung wurde verzichtet.

## 2026-07-14 | 12:14 | Codex (im Auftrag von Lewin)
Schritt: PlantUML-Code fuer das ChatGPT-Use-Case-Diagramm EasyScoot anhand von
`prompts/use-case/easyscoot-v1.md` und `lastenhefte/easyscoot.md` erzeugt und unveraendert
als v1-Original abgelegt.
Ergebnis: `ergebnisse/easyscoot/chatgpt/use-case/v1.puml`.
Beobachtung: Der Code enthaelt die drei Nutzerrollen, beide externen Systeme und elf direkt
aus dem Lastenheft abgeleitete Use Cases. Das Rechnungssystem ist korrekt an `Nutzung
beenden` beteiligt; die E-Scooter-Software uebermittelt Statusdaten und wirkt beim Starten
und Beenden des Wartungsmodus mit. Unbegruendete `include`-/`extend`-Beziehungen fehlen.

## 2026-07-14 | 12:14 | Codex (im Auftrag von Lewin)
Schritt: PlantUML-Code fuer das ChatGPT-Use-Case-Diagramm EasyLib anhand von
`prompts/use-case/easylib-v1.md` und `lastenhefte/easylib.md` erzeugt und unveraendert als
v1-Original abgelegt.
Ergebnis: `ergebnisse/easylib/chatgpt/use-case/v1.puml`.
Beobachtung: Der Code enthaelt alle drei Nutzerrollen, beide externen Systeme und 15
unterschiedliche Use Cases. `Bestand durchsuchen` und die Statuseinsicht werden jeweils von
Bibliothekar und Kunde gemeinsam genutzt. Der optionale Katalogimport ist als
`<<extend>>` modelliert; die begruendete Annahme zur mehrdeutigen Leihfristverlaengerung ist
als Notiz festgehalten.

## 2026-07-14 | 12:16 | Codex (im Auftrag von Lewin)
Schritt: Die drei neuen Use-Case-PlantUML-Codes statisch auf UML-Block, Akteurs- und
Use-Case-Anzahl, Klammern sowie Note-/End-Note-Paare geprueft und SHA-256-Pruefsummen
gebildet. Zusaetzlich wurde lokales PlantUML-Tooling gesucht.
Ergebnis: Alle drei Dateien besitzen genau einen `@startuml`-/`@enduml`-Block und
ausgeglichene Klammern. EasyRide enthaelt 2 Akteure und 5 Use Cases, EasyScoot 5 Akteure
und 11 Use Cases, EasyLib 5 Akteure und 15 Use Cases; alle Notizbloecke sind geschlossen.
Beobachtung: Weder PlantUML-Kommando noch PlantUML-JAR sind lokal vorhanden. Eine
Kompilierung und ein Rendering wurden deshalb nicht behauptet; K1 und K4 PlantUML bleiben
offen. Die Originalcodes wurden nach ihrer Ablage nicht veraendert.

## 2026-07-14 | 12:16 | Codex (im Auftrag von Lewin)
Schritt: EasyRide-`v1.puml` inhaltlich gegen Prompt und Lastenheft bewertet sowie
`evaluation.md`, `notizen.md` und Ergebnismatrix um die belegbaren PlantUML-Befunde
ergaenzt.
Ergebnis: K2 PlantUML 5/5 und K3 PlantUML 5/5; Pruefsumme und getrennte Generierung in
`notizen.md` dokumentiert. Matrixzeile easyride/chatgpt/use-case aktualisiert.
Beobachtung: Code und Direktbild sind inhaltlich deckungsgleich. K1 und K4 PlantUML bleiben
bis zu Kompilierung und Rendering offen; der Zellstatus bleibt deshalb `generiert`.

## 2026-07-14 | 12:17 | Codex (im Auftrag von Lewin)
Schritt: EasyScoot-`v1.puml` inhaltlich gegen Prompt und Lastenheft bewertet sowie
`evaluation.md`, `notizen.md` und Ergebnismatrix um die belegbaren PlantUML-Befunde
ergaenzt.
Ergebnis: K2 PlantUML 5/5 und K3 PlantUML 5/5; Pruefsumme und getrennte Generierung in
`notizen.md` dokumentiert. Matrixzeile easyscoot/chatgpt/use-case aktualisiert.
Beobachtung: Der Code korrigiert die fehlerhaften beziehungsweise mehrdeutigen
Sekundaerakteur-Zuordnungen des Direktbilds. K1 und K4 PlantUML bleiben bis zu Kompilierung
und Rendering offen; der Zellstatus bleibt `generiert`.

## 2026-07-14 | 12:18 | Codex (im Auftrag von Lewin)
Schritt: EasyLib-`v1.puml` inhaltlich gegen Prompt und Lastenheft bewertet sowie
`evaluation.md`, `notizen.md` und Ergebnismatrix um die belegbaren PlantUML-Befunde
ergaenzt.
Ergebnis: K2 PlantUML 5/5 und K3 PlantUML 5/5; Pruefsumme, Annahmen und getrennte
Generierung in `notizen.md` dokumentiert. Matrixzeile easylib/chatgpt/use-case aktualisiert.
Beobachtung: Der Code behebt die duplizierten gemeinsamen Use Cases sowie die falschen und
fehlenden Akteurszuordnungen des Direktbilds. K1 und K4 PlantUML bleiben bis zu
Kompilierung und Rendering offen; der Zellstatus bleibt `generiert`.

## 2026-07-14 | 12:20 | Codex (im Auftrag von Lewin)
Schritt: Abschliessende Konsistenzpruefung der drei neuen Use-Case-PlantUML-Codes,
Pruefsummen, eindeutigen Use-Case-Aliase, DoD-Haekchen, Matrixzeilen, Whitespace und des
Git-Index durchgefuehrt.
Ergebnis: Alle drei Pruefsummen stimmen mit `notizen.md` ueberein. EasyRide enthaelt 5,
EasyScoot 11 und EasyLib 15 eindeutige Use Cases; nur EasyLib besitzt die eine begruendete
`<<extend>>`-Beziehung. `git diff --check` meldet keine Whitespace-Fehler.
Beobachtung: Saemtliche Aenderungen sind bewusst ungestagt und uncommitted; der Git-Index
ist leer. Auf ausdruecklichen Wunsch von Lewin wurden weder Commit noch Push ausgefuehrt.
PlantUML-Rendering und damit K1/K4 PlantUML bleiben offen.

## 2026-07-14 | 13:37 | Claude (im Auftrag von Tim)
Schritt: Evaluationsdurchgang fuer die 24 vorhandenen Zellen (claude + chatgpt). PlantUML-
Rendering in der Cowork-Umgebung erneut geprueft und weiterhin blockiert (npm 403 fuer
node-plantuml, Maven/GitHub/jsDelivr/unpkg nicht erreichbar) – lokales Rendern hier nicht
moeglich. Als Ersatz statische Struktur-Pruefung aller 24 v1.puml: alle bestanden
(@startuml/@enduml paarig, Klammern balanciert, nicht abgeschnitten).
Ergebnis: evaluation/ergebnismatrix.md vollstaendig gefuellt – die 12 claude-Zeilen mit Scores
(K2/K3 + K1/K4-direkt aus den evaluation.md; claude/sequenz-PU bereits gerendert), alle 24
vorhandenen Zellen auf Status „evaluiert" gesetzt, Fussnote zum Render-Block ergaenzt. Gemini
(12 Zellen) bleibt „offen" (keine Artefakte, Regel 8).
Beobachtung: (1) K1 (Kompilierbarkeit) und K4-PlantUML bleiben fuer die 21 nicht gerenderten
Zellen offen – nur im lokalen Renderweg (z. B. IntelliJ-PlantUML-Plugin) schliessbar; statisch
sind alle 24 unauffaellig. (2) chatgpt-Zellen waren bereits von Codex bewertet (Direktbild +
K2/K3); nur Status/Matrix konsolidiert, Inhalte unveraendert. (3) claude-Scores sind
Selbstbewertungen (dieselbe KI hat generiert) – unabhaengige Gegenpruefung empfohlen; bei
claude sind PlantUML und Direktbild dasselbe Modell (Bild aus v1.puml abgeleitet). (4) Zeit vor
dem Eintrag frisch aus der Uhr gelesen (2026-07-14 13:37).

## 2026-07-14 | 14:31 | Claude (im Auftrag von Tim)
Schritt: Die (lokal erzeugten) PlantUML-Renders gesichtet und K1/K4-PlantUML fuer die 16
brauchbaren Renders bewertet; ergebnismatrix.md entsprechend gefuellt (K1-PU/K4-PU eingetragen,
Abschnitte „Kernbefunde" und „Offene Punkte" ergaenzt).
Ergebnis: evaluation/ergebnismatrix.md aktualisiert. Befunde: alle 16 gerenderten v1.puml
kompilieren fehlerfrei (K1-PU=5). K4-PU: ChatGPT meist 5 (inkl. loop-Fragment
easyride/chatgpt/sequenz), Claude 4-5, Ausnahme die Claude-Klassendiagramme mit ausufernden
Auto-Layout-Boegen (easyride 3, easyscoot 4). Vergleich bestaetigt: ChatGPTs PlantUML-Code ist
inhaltlich korrekt (K2-PU=5), waehrend die direkten Bilder teils stark abfallen
(easyride/chatgpt/klassendiagramm direkt K2=2, Code korrekt).
Beobachtung: 8 Renders fehlen/fehlerhaft: easyride/chatgpt/aktivitaet (kein Bild) sowie alle
easylib-Zellen ausser claude/sequenz (Datei v1-PlantUML.png, 0 Byte – falsche Gross-/
Kleinschreibung + leerer Render). Nach Neurendern (als v1-plantuml.png) K1/K4-PlantUML dieser 8
Zellen analog nachtragen. Die einzelnen evaluation.md tragen K1/K4-PlantUML noch als
„offen/ausstehend"; die Matrix ist der aktuelle Gesamtstand – Propagierung in die einzelnen
evaluation.md ist der offene Folgeschritt. Zeit frisch gelesen (2026-07-14 14:31).

## 2026-07-14 | 14:45 | Claude (im Auftrag von Tim)
Schritt: Die 8 zuvor fehlenden/fehlerhaften Renders sind nachgerendert (jetzt korrekt als
v1-plantuml.png, 15–46 KB) – gesichtet und bewertet. ergebnismatrix.md final aktualisiert: alle
24 Zellen mit vollstaendigen PU- und Direkt-Scores.
Ergebnis: evaluation/ergebnismatrix.md final. Alle 24 v1.puml kompilieren fehlerfrei (K1-PU=5).
Neu bewertet: easyride/chatgpt/aktivitaet (K4-PU 5) und alle easylib-Zellen (claude
klassen/use-case K4-PU 4, aktivitaet 5, sequenz 4; chatgpt klassen/aktivitaet/sequenz K4-PU 5,
use-case K4-PU 3 – viele Kreuzungen).
Beobachtung: Keine Render-/Kompilierfehler mehr; K1 ist damit fuer beide KIs ueber alle vier
Diagrammtypen vollstaendig bestaetigt. Verbleibend offen: Gemini (keine Artefakte) sowie die
Propagierung der K1/K4-PU-Scores aus der Matrix in die einzelnen evaluation.md. Zeit frisch
gelesen (2026-07-14 14:45).
