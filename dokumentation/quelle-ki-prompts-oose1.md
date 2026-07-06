> **Archivierte Quelle** – unverändert übernommener Upload `KI-Prompts-EasyScoot-EasyRide-EasyLib.md`
> (übernommen am 06.07.2026, Dateiname an Namenskonvention angepasst). Grundlage der generischen
> Prompt-Bibliothek `prompts/<typ>/v1.md`; die Anpassungen an die Repo-Methodik sind dort im
> Abschnitt „Änderungen gegenüber Vorversion + Begründung" dokumentiert.

---

# KI-Prompts für die Lastenhefte EasyScoot, EasyRide und EasyLib

**Kurs:** Objektorientierte Softwaretechnik I (Q3 2025)
**Ziel:** Für jedes der drei Lastenhefte werden Prompts bereitgestellt, mit denen eine KI (z. B. Claude oder ChatGPT) folgende UML-Artefakte erzeugt:

1. ein **Klassendiagramm**
2. ein **Use-Case-Diagramm** mit mindestens **5 Use Cases**
3. ein **Aktivitätsdiagramm** mit mindestens **5 Aktivitäten**
4. ein **Sequenzdiagramm** mit mindestens **5 Methodenaufrufen**

Zu jedem Prompt ist ausführlich dokumentiert, **warum** er so aufgebaut und formuliert ist.

---

## Inhaltsverzeichnis

1. [Anleitung: So werden die Prompts verwendet](#anleitung)
2. [Allgemeine Design-Prinzipien der Prompts (übergreifende Begründung)](#prinzipien)
3. [EasyScoot – Prompts und Begründungen](#easyscoot)
4. [EasyRide – Prompts und Begründungen](#easyride)
5. [EasyLib – Prompts und Begründungen](#easylib)
6. [Qualitätskontrolle der KI-Ergebnisse](#qualitaet)

---

<a id="anleitung"></a>
## 1. Anleitung: So werden die Prompts verwendet

Pro Projekt gibt es **einen Basis-Prompt** und **vier Diagramm-Prompts**. Die Prompts sind als *eine zusammenhängende Konversation* konzipiert:

1. Neuen Chat öffnen und den **Basis-Prompt** senden. Er enthält eine Systembeschreibung, die den Inhalt des Lastenhefts vollständig, aber in eigenen Worten wiedergibt (Begründung in Abschnitt 2.2).
2. Danach die vier **Diagramm-Prompts** nacheinander in denselben Chat senden – erst wenn das vorherige Diagramm geprüft wurde.
3. Den ausgegebenen PlantUML-Code z. B. unter [plantuml.com](https://www.plantuml.com/plantuml/uml/) oder mit der VS-Code-Erweiterung „PlantUML" rendern.
4. Jedes Diagramm gegen das Lastenheft prüfen (Checkliste in Abschnitt 6) und bei Fehlern gezielt nachbessern lassen, z. B.: *„Im Klassendiagramm fehlt die Multiplizität zwischen X und Y, korrigiere das."*

**Warum eine Konversation statt vier unabhängiger Prompts?** Die Diagramme müssen zueinander konsistent sein: Die Methodenaufrufe im Sequenzdiagramm müssen zu den Klassen und Operationen des Klassendiagramms passen, die Aktivitäten und Szenarien zu den Use Cases. Sendet man jeden Prompt in einen frischen Chat, erfindet die KI jedes Mal neue Klassen- und Methodennamen, und die Abgabe wirkt zusammengestückelt. In einer Konversation bleibt der Kontext (Lastenheft + bereits erzeugte Diagramme) erhalten und die KI referenziert ihre eigenen früheren Modellelemente.

---

<a id="prinzipien"></a>
## 2. Allgemeine Design-Prinzipien der Prompts (übergreifende Begründung)

Alle zwölf Diagramm-Prompts folgen demselben Bauplan. Die folgenden Entscheidungen gelten übergreifend; in den Projektkapiteln wird nur noch das Projektspezifische begründet.

### 2.1 Rollenzuweisung („Du bist ein erfahrener Softwareanalytiker …")

Jeder Basis-Prompt beginnt mit einer Rollenzuweisung. KI-Modelle passen Stil, Detailtiefe und Fachvokabular an die zugewiesene Rolle an. Ohne Rolle antworten sie oft auf dem Niveau eines allgemeinen Erklärtexts; mit der Rolle „Softwareanalytiker und UML-Modellierer" nutzen sie korrekte UML-Terminologie (Multiplizitäten, Assoziationen, Lebenslinien) und treffen Modellierungsentscheidungen, statt nur den Text nachzuerzählen.

### 2.2 Systembeschreibung in eigenen Worten statt Lastenheft-Kopie

Jeder Basis-Prompt enthält den vollständigen *Inhalt* des jeweiligen Lastenhefts – aber bewusst als **Zusammenfassung in eigenen Worten** („Systembeschreibung"), nicht als wörtliche Kopie. Gründe:

- **Eigenleistung und Verständnisnachweis:** Die Prompts sind Teil der eigenen Abgabe. Eine Paraphrase erzwingt, das Lastenheft wirklich durchdrungen zu haben – wer beim Zusammenfassen eine Regel falsch wiedergibt, merkt es beim Gegenlesen. Eine 1:1-Kopie der Kursunterlagen wäre dagegen keine eigene Leistung und ließe sich beliebig ohne Verständnis erzeugen.
- **Bessere Struktur für die KI:** Die Originaltexte verstreuen zusammengehörige Informationen (z. B. stehen die Statusattribute der E-Scooter erst im Flottenmanager-Absatz). Die Systembeschreibungen ordnen die Inhalte neu – nach Ablauf, Rollen, Regeln und Datenmodell – und erleichtern der KI damit die Modellbildung.
- **Grounding bleibt erhalten:** Die Hauptgefahr einer Paraphrase ist Informationsverlust – was im Prompt fehlt, kann die KI nicht modellieren, und was ungenau formuliert ist, modelliert sie falsch. Deshalb gilt: Alle modellierungsrelevanten **Fakten** werden vollständig übernommen (jedes Attribut, jeder Zahlenwert wie der 50-%-Filter, jede Geschäftsregel, jede Werteliste), nur der Wortlaut und die Reihenfolge sind neu. Jede Systembeschreibung wurde nach dem Formulieren Punkt für Punkt gegen das Original geprüft.
- **Unabhängigkeit:** Der Prompt funktioniert weiterhin per Copy-Paste in jedem KI-Tool, ohne dass ein PDF-Upload nötig oder möglich sein muss.

Die Abgrenzung der Systembeschreibung durch `---`-Trennlinien verhindert, dass die KI Arbeitsanweisungen und Systeminhalt vermischt (z. B. Aufzählungen der Beschreibung als Arbeitsanweisung missversteht).

### 2.3 PlantUML als Ausgabeformat

Alle Prompts fordern die Diagramme als **PlantUML-Code** an, nicht als Bild oder Textbeschreibung. Begründung:

- KI-Chatbots können keine verlässlichen Bilddiagramme zeichnen, aber sehr zuverlässig PlantUML erzeugen – das ist ein Textformat, das sich deterministisch in ein korrektes UML-Diagramm rendern lässt.
- Der Code ist **editierbar**: Fehler lassen sich von Hand oder per Folge-Prompt korrigieren, ohne alles neu zu generieren.
- PlantUML beherrscht alle vier geforderten Diagrammtypen mit korrekter UML-2-Notation. (Alternative: Mermaid – wird von manchen Tools direkt gerendert, unterstützt aber Aktivitätsdiagramme nur eingeschränkt als Flowcharts, daher fiel die Wahl auf PlantUML.)

### 2.4 Explizite Mindestzahlen als Abnahmekriterien

Die Vorgaben „mindestens 5 Use Cases / 5 Aktivitäten / 5 Methodenaufrufe" stehen wörtlich und **fett hervorgehoben** in den Prompts. KI-Modelle neigen bei UML-Aufgaben zu minimalistischen Beispielen (3 Use Cases, 2 Nachrichten). Eine explizite, zählbare Untergrenze ist ein objektives Abnahmekriterium: Man kann das Ergebnis mechanisch prüfen und die Anforderung notfalls wörtlich wiederholen („Es sind nur 4 Aktivitäten, ergänze …").

### 2.5 Positiv- und Negativ-Constraints (Leitplanken)

Jeder Prompt enthält Leitplanken wie „Verwende ausschließlich Inhalte aus dem Lastenheft" und „Erfinde keine zusätzlichen Features". Das adressiert die zwei häufigsten KI-Fehler bei Modellierungsaufgaben:

1. **Hinzudichten** von branchenüblichen, aber nicht geforderten Funktionen (Login-Flows, Bezahlsysteme, Admin-Panels).
2. **Weglassen** unbequemer Details (z. B. die Kapazitätsregel bei EasyRide-Routen), weil sie das Modell komplizierter machen.

Wo nötig, nennen die Prompts die kritischen Details namentlich („bilde die Regel ab, dass …"). Das ist gezieltes *Aufmerksamkeitslenken*: Was im Prompt explizit steht, wird selten vergessen.

### 2.6 Annahmen und Unklarheiten offenlegen

Jeder Basis-Prompt verlangt: „Liste am Ende jeder Antwort deine Annahmen und erkannte Unklarheiten im Lastenheft auf." Die Lastenhefte sind – wie in der Vorlesung (Kapitel 4) betont – bewusst unvollständig und stellenweise mehrdeutig. Eine KI trifft an solchen Stellen stillschweigend Entscheidungen. Die Offenlegungspflicht macht diese Entscheidungen sichtbar, sodass man sie in der Übung begründen oder korrigieren kann. Nebeneffekt: Die Annahmenliste ist gutes Material für die Ergebnispräsentation.

### 2.7 Selbstprüfung vor der Ausgabe

Die Diagramm-Prompts enden mit einer kurzen Checkliste („Prüfe vor der Ausgabe: …"). Das nutzt den Effekt, dass KI-Modelle deutlich weniger Fehler machen, wenn sie angewiesen werden, ihre Antwort vor der Ausgabe gegen konkrete Kriterien zu prüfen (Self-Checking). Die Checkpunkte sind pro Diagrammtyp gewählt: Multiplizitäten beim Klassendiagramm, Systemgrenze beim Use-Case-Diagramm, Start-/Endknoten beim Aktivitätsdiagramm, synchrone Aufrufe und Antworten beim Sequenzdiagramm.

### 2.8 Deutsch als Modellierungssprache

Alle Bezeichner (Klassen, Use Cases, Aktivitäten, Methoden) werden auf Deutsch gefordert, weil die Lastenhefte und die Abgabe deutschsprachig sind. Ohne diese Vorgabe mischen KI-Modelle gern englische Bezeichner (`Customer`, `bookRide()`) ein, was in der Präsentation inkonsistent wirkt und die Zuordnung zum Lastenheft erschwert.

### 2.9 Festgelegte Szenarien für Aktivitäts- und Sequenzdiagramm

Für Aktivitäts- und Sequenzdiagramm legen die Prompts das zu modellierende Szenario **fest** (z. B. „Fahrt buchen" bei EasyRide), statt die Wahl der KI zu überlassen. Gründe:

- Überlässt man die Wahl der KI, nimmt sie oft das trivialste Szenario („Konto anlegen"), das die Mindestzahlen kaum hergibt.
- Die gewählten Szenarien sind jeweils der **fachliche Kern** des Systems und decken die interessanten Entscheidungen und Systemschnittstellen ab – genau das, was in einer Übungspräsentation diskutiert wird.
- Ein festes Szenario macht die Ergebnisse zweier Durchläufe (oder zweier Teammitglieder) vergleichbar.

Welches Szenario pro Projekt gewählt wurde und warum, steht in der jeweiligen Begründung.

---

<a id="easyscoot"></a>
## 3. EasyScoot – Prompts und Begründungen

**Systemkontext:** E-Scooter-Verleih mit Smartphone-Buchung. Drei menschliche Nutzergruppen (Kunde, Flottenmanager, Service-Mitarbeiter) und zwei technische Schnittstellen (E-Scooter-Software per Mobilfunk, existierendes Rechnungssystem).

### 3.1 Basis-Prompt (zuerst senden)

```text
Du bist ein erfahrener Softwareanalytiker und UML-Modellierer. Wir analysieren
gemeinsam das Lastenheft „EasyScoot" aus einem Hochschulkurs zur
objektorientierten Softwaretechnik und erstellen daraus schrittweise
UML-Diagramme (Klassendiagramm, Use-Case-Diagramm, Aktivitätsdiagramm,
Sequenzdiagramm).

Regeln für die gesamte Konversation:
1. Verwende ausschließlich Inhalte aus der folgenden Systembeschreibung; sie
   gibt das Lastenheft vollständig in eigenen Worten wieder. Erfinde keine
   zusätzlichen Features (z. B. keine Bezahlfunktion in der App, kein
   Bewertungssystem, keine Registrierung per Social Login).
2. Alle Bezeichner (Klassen, Attribute, Methoden, Use Cases, Aktivitäten) sind
   auf Deutsch.
3. Gib jedes Diagramm als PlantUML-Code in einem Codeblock aus, gefolgt von
   einer kurzen Erläuterung deiner Modellierungsentscheidungen.
4. Verwende korrekte UML-2-Notation.
5. Liste am Ende jeder Antwort deine Annahmen und erkannte Unklarheiten in
   den Anforderungen auf.
6. Achte darauf, dass alle Diagramme zueinander konsistent sind: gleiche
   Klassen-, Akteurs- und Methodennamen über alle Diagramme hinweg.

Bestätige kurz, dass du die Systembeschreibung gelesen hast, und nenne die Akteure und
externen Systeme, die du erkennst. Erstelle noch kein Diagramm.

---
SYSTEMBESCHREIBUNG „EasyScoot" (Inhalt des Lastenhefts in eigenen Worten):

EasyScoot ist die neu zu entwickelnde Software eines E-Scooter-Verleihs. In
einer Stadt stehen E-Scooter an wechselnden Orten bereit; Kunden buchen sie
per Smartphone, schalten sie frei, fahren damit und stellen sie an einem
beliebigen Zielort wieder ab.

Ablauf aus Kundensicht: Zuerst legt der Kunde ein Kundenkonto an, in dem
Vorname, Name, Anschrift (Straße, Hausnummer, PLZ, Ort) und E-Mail-Adresse
gespeichert werden. Danach kann er abfragen, welche freien E-Scooter sich in
seiner Nähe befinden; das System zeigt eine Liste mit Standort, Ladestand
und geschätzter restlicher Fahrzeit in Minuten. Der Kunde begibt sich zum
gewählten E-Scooter, bucht ihn dort und schaltet ihn frei. Nach der Fahrt
beendet er die Nutzung per Smartphone und erhält eine Zusammenfassung der
Fahrt mit Dauer, gefahrenen Kilometern, verbrauchten Wattstunden und Preis.
Wichtig: Den Preis berechnet nicht EasyScoot selbst, sondern ein bereits
existierendes Rechnungssystem, das lediglich angebunden wird.

Technik der E-Scooter: Jeder E-Scooter trägt eine bereits fertig entwickelte
Software, die per Mobilfunk in regelmäßigen Abständen Position, Ladezustand
und Fahrstatus (stehend oder fahrend) an EasyScoot meldet. Als Stammdaten
sind je E-Scooter Marke, Modell, Batteriekapazität (in Wattstunden) und der
durchschnittliche Verbrauchskoeffizient (Wattstunden pro Kilometer)
hinterlegt.

Weitere Rollen, jeweils mit eigenem Nutzerkonto:
- Flottenmanager können jederzeit eine Liste aller E-Scooter mit sämtlichen
  Informationen abrufen: ID, Position, Ladestand, geschätzte übrige
  Fahrzeit, Fahrstatus (stehend/fahrend), Leihstatus (in Benutzung oder
  nicht) und Wartungsstatus (in Wartung / nicht in Wartung).
- Service-Mitarbeiter sehen ebenfalls die Gesamtliste und zusätzlich eine
  gefilterte Liste aller E-Scooter mit einem Ladestand von höchstens 50 %.
  E-Scooter mit wenig Ladung bringen sie zu Ladestationen. Für Transport
  und Ladevorgang versetzen sie den E-Scooter in einen Wartungsmodus: Der
  E-Scooter meldet sich per Mobilfunk ab, und sein Wartungsstatus wird in
  EasyScoot auf „in Wartung" gesetzt. Beim Beenden der Wartung meldet sich
  der E-Scooter per Mobilfunk wieder an, und der Status wechselt auf „nicht
  in Wartung". Außerdem nehmen Service-Mitarbeiter neue E-Scooter in die
  Flotte auf und mustern alte aus.
---
```

**Begründung (projektspezifisch):**

- Die Negativliste nennt bewusst *konkrete* naheliegende Halluzinationen (Bezahlfunktion, Bewertungssystem): Bei Sharing-Apps ergänzen KI-Modelle diese Features fast reflexhaft, weil reale Vorbilder (Tier, Lime, Bolt) sie haben. Das Lastenheft delegiert die Preisberechnung aber ausdrücklich an ein *existierendes* Rechnungssystem – die Bezahlung ist also außerhalb des Systems.
- Der Auftrag „nenne die Akteure und externen Systeme" ist ein bewusster **Verständnis-Check vor dem ersten Diagramm**: EasyScoot hat als einziges der drei Projekte zwei externe Systeme (E-Scooter-Software, Rechnungssystem). Erkennt die KI diese hier korrekt, sind spätere Fehler (z. B. Rechnungssystem als interne Klasse) unwahrscheinlich. „Erstelle noch kein Diagramm" verhindert, dass die KI ungefragt vorprescht und dabei die Diagramm-Prompts leerlaufen.

### 3.2 Prompt: Klassendiagramm

```text
Erstelle ein UML-Klassendiagramm für EasyScoot als PlantUML-Code.

Anforderungen:
- Modelliere mindestens: Kunde, E-Scooter, Fahrt, Flottenmanager,
  Service-Mitarbeiter sowie das externe Rechnungssystem als Schnittstelle.
- Übernimm alle in der Systembeschreibung genannten Attribute mit sinnvollen Datentypen,
  u. a.: Kunde (Vorname, Name, Straße, Hausnummer, PLZ, Ort, Emailadresse),
  E-Scooter (ID, Marke, Modell, Batteriekapazität in Wattstunden,
  Verbrauchskoeffizient in Wh/km, Position, Ladezustand, Fahrstatus,
  Leihstatus, Wartungsstatus), Fahrt (Dauer, gefahrene Kilometer, verbrauchte
  Wattstunden, Preis).
- Modelliere Fahrstatus, Leihstatus und Wartungsstatus als Enumerationen mit
  den Werten aus der Systembeschreibung.
- Prüfe, ob Kunde, Flottenmanager und Service-Mitarbeiter eine gemeinsame
  Oberklasse (z. B. Nutzerkonto) haben sollten, und begründe deine
  Entscheidung.
- Versieh alle Assoziationen mit Multiplizitäten und, wo sinnvoll, mit
  Leserichtung oder Rollennamen.
- Ergänze zentrale Methoden an den Klassen, mindestens die, die für Buchen,
  Freischalten, Nutzung beenden und Wartungsmodus nötig sind.

Prüfe vor der Ausgabe: Hat jede Assoziation Multiplizitäten? Sind alle
Attribute aus der Systembeschreibung enthalten? Ist das Rechnungssystem als externe
Schnittstelle und nicht als normale Systemklasse modelliert?
```

**Begründung:**

- **Attributliste gebündelt im Prompt:** Das Original-Lastenheft verstreut die Attribute über mehrere Absätze (Kundendaten und Scooter-Stammdaten in der Ablaufbeschreibung, Statusdaten erst beim Flottenmanager). Die Systembeschreibung ordnet das bereits; der Diagramm-Prompt bündelt die Attribute zusätzlich an einer Stelle, weil KI-Modelle am zuverlässigsten übernehmen, was kompakt beieinandersteht. Das ist kein Vorsagen der Lösung, sondern Kompensation der Textstruktur der Quelle – die Modellierungsarbeit (Klassen schneiden, Assoziationen, Multiplizitäten) bleibt bei der KI.
- **Enumerationen explizit gefordert:** Fahrstatus (stehend/fahrend), Leihstatus (in Benutzung/nicht), Wartungsstatus (in Wartung/nicht in Wartung) sind klassische Enum-Kandidaten. Ohne Hinweis modellieren KIs sie oft als `String` – fachlich schwächer und in der Übung ein typischer Kritikpunkt.
- **Oberklassen-Frage offen gestellt statt vorgegeben:** Ob Kunde/Flottenmanager/Service-Mitarbeiter unter „Nutzerkonto" generalisiert werden, ist eine echte Designentscheidung (das Lastenheft sagt nur, dass sie „über entsprechende Nutzerkonten verfügen"). Der Prompt erzwingt keine Lösung, sondern eine **begründete** Entscheidung – das liefert Diskussionsstoff für die Präsentation und zeigt, dass Modellieren Abwägen ist.
- **Rechnungssystem als Schnittstelle:** Der häufigste Fehler bei diesem Lastenheft ist, das Rechnungssystem als interne Klasse mit Attributen zu modellieren. Der Selbstprüfungs-Punkt zielt genau darauf.

### 3.3 Prompt: Use-Case-Diagramm

```text
Erstelle ein UML-Use-Case-Diagramm für EasyScoot als PlantUML-Code mit
mindestens 5 Use Cases.

Anforderungen:
- Akteure: Kunde, Flottenmanager, Service-Mitarbeiter sowie die externen
  Systeme E-Scooter (Mobilfunk-Software) und Rechnungssystem als
  Sekundärakteure, wo sie an Use Cases beteiligt sind.
- Zeichne eine Systemgrenze mit dem Namen „EasyScoot"; die Akteure stehen
  außerhalb.
- Leite die Use Cases direkt aus der Systembeschreibung ab, u. a.: Kundenkonto
  erstellen, verfügbare E-Scooter in der Nähe abfragen, E-Scooter buchen und
  freischalten, Nutzung beenden, Liste aller E-Scooter einsehen, gefilterte
  Liste (Ladestand ≤ 50 %) einsehen, Wartungsmodus starten/beenden, E-Scooter
  in Flotte aufnehmen, E-Scooter ausmustern.
- Verwende <<include>> oder <<extend>> nur, wenn es fachlich klar begründbar
  ist, und erkläre jede Verwendung. Im Zweifel lieber weglassen.

Prüfe vor der Ausgabe: Sind es mindestens 5 Use Cases? Stehen alle Akteure
außerhalb der Systemgrenze? Ist jeder Use Case aus Akteurssicht als
Verrichtung formuliert (Verb + Objekt)?
```

**Begründung:**

- **Kandidatenliste statt freier Suche:** Das Lastenheft enthält deutlich mehr als 5 Use Cases. Die Liste im Prompt stellt sicher, dass die KI die *richtigen* nimmt (die explizit geforderten Systemleistungen) statt erfundener Verwaltungsfunktionen. Sie ist bewusst als „u. a." formuliert, damit die KI eine begründete Auswahl treffen darf.
- **`<<include>>`/`<<extend>>` gedrosselt:** KI-Modelle überdekorieren Use-Case-Diagramme notorisch mit include/extend-Beziehungen, oft falsch herum. Da falsche Stereotype in der Übung schwerer wiegen als fehlende, gilt: nur mit Begründung, im Zweifel weglassen.
- **Sekundärakteure gefordert:** Dass E-Scooter und Rechnungssystem als Akteure auftauchen (z. B. am Use Case „Nutzung beenden"), zeigt das Verständnis von Systemgrenzen – ein Kernthema aus Kapitel 4 der Vorlesung.
- **Formulierungsregel „Verb + Objekt":** Erzwingt die in der Vorlesung gelehrte Verrichtungsform („E-Scooter buchen" statt „Buchung").

### 3.4 Prompt: Aktivitätsdiagramm

```text
Erstelle ein UML-Aktivitätsdiagramm für EasyScoot als PlantUML-Code für das
Szenario „E-Scooter ausleihen und nutzen" – von der Suche nach einem E-Scooter
bis zur Anzeige der Fahrtzusammenfassung.

Anforderungen:
- Mindestens 5 Aktivitäten.
- Enthalten sein müssen mindestens: verfügbare E-Scooter abfragen, E-Scooter
  auswählen, zum Standort begeben, E-Scooter buchen und freischalten,
  E-Scooter nutzen, Nutzung beenden, Zusammenfassung anzeigen.
- Mindestens eine Entscheidung (z. B.: Ist ein passender E-Scooter in der
  Nähe verfügbar?) mit beschrifteten Kanten.
- Verwende Aktivitätsbereiche (Swimlanes) für Kunde, EasyScoot-System und
  Rechnungssystem, um zu zeigen, wer welche Aktivität ausführt.
- Beginne mit einem Startknoten und ende mit einem Endknoten.

Prüfe vor der Ausgabe: Sind es mindestens 5 Aktivitäten? Hat jede Entscheidung
beschriftete Ausgänge? Liegt die Preisberechnung in der Swimlane des
Rechnungssystems?
```

**Begründung:**

- **Szenariowahl:** „Ausleihen und nutzen" ist der fachliche Kernprozess des Lastenhefts (drei volle Absätze) und liefert von allein weit mehr als 5 Aktivitäten plus eine natürliche Entscheidung. Alternativen wie „Konto erstellen" wären zu trivial, „Wartungsmodus" zu randständig.
- **Swimlanes gefordert:** Das Szenario überschreitet zweimal Systemgrenzen (Kunde ↔ EasyScoot ↔ Rechnungssystem). Swimlanes machen sichtbar, dass die Preisberechnung *nicht* in EasyScoot stattfindet – dieselbe Abgrenzung, die schon im Klassen- und Use-Case-Diagramm betont wurde. Konsistenz über Diagramme hinweg ist ein Bewertungskriterium.
- **„Zum Standort begeben" in der Aktivitätenliste:** Bewusst enthalten, weil es eine rein physische Aktivität des Kunden ohne Systembeteiligung ist – ein guter Prüfstein, ob Swimlanes verstanden wurden (sie gehört in die Kunden-Lane).
- **Start-/Endknoten explizit:** PlantUML erzwingt sie nicht; KI-generierte Aktivitätsdiagramme lassen sie gern weg, was formal ein Notationsfehler ist.

### 3.5 Prompt: Sequenzdiagramm

```text
Erstelle ein UML-Sequenzdiagramm für EasyScoot als PlantUML-Code für das
Szenario „Kunde beendet die Nutzung eines E-Scooters".

Anforderungen:
- Mindestens 5 Methodenaufrufe.
- Beteiligte Lebenslinien: Kunde (bzw. seine Smartphone-App als Akteur), das
  EasyScoot-System, der E-Scooter (externe Mobilfunk-Software), die Fahrt und
  das Rechnungssystem.
- Der Ablauf muss fachlich zur Systembeschreibung passen: Nutzung beenden →
  E-Scooter sperren/Status aktualisieren → Fahrtdaten (Dauer, Kilometer,
  Wattstunden) ermitteln → Preis vom Rechnungssystem berechnen lassen →
  Zusammenfassung an den Kunden zurückgeben.
- Verwende synchrone Aufrufe mit Antwortpfeilen und sinnvolle
  Methodensignaturen mit Parametern, z. B. berechnePreis(dauer, kilometer,
  wattstunden).
- Nutze dieselben Klassen- und Methodennamen wie im Klassendiagramm aus
  dieser Konversation; ergänze fehlende Methoden dort gedanklich und weise
  darauf hin.

Prüfe vor der Ausgabe: Sind es mindestens 5 Methodenaufrufe? Hat jeder
synchrone Aufruf eine Antwort? Stimmen die Namen mit dem Klassendiagramm
überein?
```

**Begründung:**

- **Szenariowahl:** „Nutzung beenden" ist die einzige Stelle des Lastenhefts, an der *alle* Systemteile zusammenspielen (App, EasyScoot, Scooter-Mobilfunk, Rechnungssystem) – ideal, um mit wenigen Lebenslinien auf ≥ 5 fachlich echte Methodenaufrufe zu kommen, statt Aufrufe künstlich aufzublähen.
- **Ablauf grob vorgegeben, Signaturen frei:** Der Prompt fixiert die fachliche Reihenfolge (aus dem Lastenheft ableitbar), überlässt aber Methodennamen und Parameter der KI. So bleibt das Ergebnis prüfbar korrekt, ohne dass der Prompt das Diagramm faktisch vorwegnimmt.
- **Konsistenzpflicht mit dem Klassendiagramm:** Wichtigster Punkt des Prompts – Sequenzdiagramme, deren Methoden im Klassendiagramm nicht existieren, sind der häufigste Konsistenzfehler in Abgaben. Der Zusatz „weise darauf hin" erzeugt zudem eine saubere Änderungsliste für das Klassendiagramm.
- **Beispielsignatur `berechnePreis(dauer, kilometer, wattstunden)`:** Ein einzelnes Beispiel kalibriert das Abstraktionsniveau (fachliche Parameter statt `data: Object`), ohne alle Signaturen vorzugeben.

---

<a id="easyride"></a>
## 4. EasyRide – Prompts und Begründungen

**Systemkontext:** Ridesharing-System mit Fahrzeugflotte, Haltepunkt-Netz (ungerichteter Graph mit Fahrzeiten) und dynamischer Routenplanung. Akteure: Kunde/Fahrgast (Smartphone) und Fahrer (Tablet). Fachlicher Kern ist die **Route** mit der Kapazitätsregel (nie mehr Fahrgäste als Sitzplätze).

### 4.1 Basis-Prompt (zuerst senden)

```text
Du bist ein erfahrener Softwareanalytiker und UML-Modellierer. Wir analysieren
gemeinsam das Lastenheft „EasyRide" aus einem Hochschulkurs zur
objektorientierten Softwaretechnik und erstellen daraus schrittweise
UML-Diagramme (Klassendiagramm, Use-Case-Diagramm, Aktivitätsdiagramm,
Sequenzdiagramm).

Regeln für die gesamte Konversation:
1. Verwende ausschließlich Inhalte aus der folgenden Systembeschreibung; sie
   gibt das Lastenheft vollständig in eigenen Worten wieder. Erfinde keine
   zusätzlichen Features (z. B. keine Bezahlung, keine Bewertung, kein
   Live-GPS-Tracking über das Beschriebene hinaus).
2. Alle Bezeichner (Klassen, Attribute, Methoden, Use Cases, Aktivitäten) sind
   auf Deutsch.
3. Gib jedes Diagramm als PlantUML-Code in einem Codeblock aus, gefolgt von
   einer kurzen Erläuterung deiner Modellierungsentscheidungen.
4. Verwende korrekte UML-2-Notation.
5. Liste am Ende jeder Antwort deine Annahmen und erkannte Unklarheiten in
   den Anforderungen auf.
6. Achte darauf, dass alle Diagramme zueinander konsistent sind: gleiche
   Klassen-, Akteurs- und Methodennamen über alle Diagramme hinweg.
7. Behandle diese drei Fachregeln als unverhandelbar und bilde sie in den
   Diagrammen ab:
   a) Das Netz aus Haltepunkten ist ein ungerichteter Graph; jede direkte
      Verbindung hat eine durchschnittliche Fahrzeit.
   b) Auf einer Route darf die Anzahl Fahrgäste nie die Sitzplätze des
      Fahrzeugs übersteigen.
   c) Jede Route beginnt und endet am Haltepunkt „Zentrale", der nicht zum
      Ein- und Aussteigen genutzt werden darf.

Bestätige kurz, dass du die Systembeschreibung gelesen hast, und nenne die Akteure
sowie die zentralen Fachbegriffe (Haltepunkt, Verbindung, Route, Fahrzeug,
Fahrgast), wie du sie verstanden hast. Erstelle noch kein Diagramm.

---
SYSTEMBESCHREIBUNG „EasyRide" (Inhalt des Lastenhefts in eigenen Worten):

EasyRide ist die zu entwickelnde Software für ein städtisches
Ridesharing-System: Eine Flotte von Fahrzeugen befördert Fahrgäste zwischen
festen Haltepunkten, wobei ein Fahrzeug gleichzeitig mehrere Fahrgäste mit
jeweils unterschiedlichen Start- und Zielhaltepunkten transportieren kann.
Die Fahrzeuge unterscheiden sich in ihrer Anzahl an Sitzplätzen.

Das Haltepunktnetz: Gehalten werden darf ausschließlich an definierten
Haltepunkten. Die Haltepunkte und ihre direkten Verbindungen bilden einen
ungerichteten Graphen – jede Verbindung ist in beide Richtungen befahrbar,
Einbahnstraßen existieren nicht. Zu jeder direkten Verbindung ist eine
durchschnittliche Fahrzeit hinterlegt.

Routen: Bucht ein Kunde eine Fahrt, wird dafür entweder eine neue Route für
ein Fahrzeug angelegt oder eine bestehende Route verändert bzw. erweitert.
Eine Route ist eine geordnete Liste von Haltepunkten, die das Fahrzeug
nacheinander anfährt, um Fahrgäste aufzunehmen und abzusetzen; sie legt für
jeden Halt fest, welche Fahrgäste dort zusteigen und welche aussteigen. Zwei
Regeln gelten dabei ausnahmslos:
1. Zu keinem Zeitpunkt dürfen mehr Fahrgäste eingeplant sein, als das
   Fahrzeug Sitzplätze hat.
2. Jede Route beginnt und endet am Sonderhaltepunkt „Zentrale", an dem kein
   Ein- oder Ausstieg möglich ist.

Leistungen für Kunden (z. B. per Smartphone):
- eine Fahrt von einem Start- zu einem Zielort buchen
- vor Fahrtantritt die übrige Wartezeit erfahren (die Zeit, bis das Fahrzeug
  den gewählten Startpunkt erreicht)
- nach Fahrtantritt die übrige Fahrzeit bis zum Ziel erfahren, abhängig vom
  zuletzt erreichten Haltepunkt

Leistungen für Fahrer (per Tablet im Fahrzeug):
- den nächsten anzufahrenden Haltepunkt abfragen, einschließlich der Namen
  der dort aufzunehmenden und abzusetzenden Fahrgäste
- das Erreichen des nächsten Haltepunkts bestätigen
---
```

**Begründung (projektspezifisch):**

- **Regel 7 (unverhandelbare Fachregeln) gibt es nur bei EasyRide.** Dieses Lastenheft ist das strukturell anspruchsvollste der drei: Graph, Kapazitätsinvariante und Zentrale-Sonderregel sind *Invarianten*, keine Funktionen – genau solche Regeln lassen KI-Modelle beim Modellieren am ehesten fallen, weil sie in keiner Funktionsliste auftauchen. Sie einmal zentral im Basis-Prompt zu verankern wirkt auf alle vier Diagramme, statt sie in jedem Diagramm-Prompt wiederholen zu müssen.
- **Fachbegriffs-Check statt nur Akteurs-Check:** Bei EasyScoot war die Gefahr, externe Systeme zu übersehen; bei EasyRide ist die Gefahr, die Begriffe Route/Verbindung/Haltepunkt zu verwechseln (eine Route ist eine *Liste von Haltepunkten*, eine Verbindung eine *Graphkante mit Fahrzeit* – zwei völlig verschiedene Dinge). Der Prompt lässt die KI ihr Verständnis vor dem ersten Diagramm formulieren, damit Begriffsfehler früh auffallen.
- **Negativliste angepasst:** Bei Ridesharing halluzinieren KIs typischerweise Bezahlung, Fahrer-Bewertungen und Echtzeit-GPS. Das Lastenheft arbeitet aber ausschließlich mit hinterlegten Durchschnittsfahrzeiten und bestätigten Haltepunkten – deshalb wird Live-Tracking ausdrücklich ausgeschlossen.

### 4.2 Prompt: Klassendiagramm

```text
Erstelle ein UML-Klassendiagramm für EasyRide als PlantUML-Code.

Anforderungen:
- Modelliere mindestens: Haltepunkt, Verbindung (zwischen genau zwei
  Haltepunkten, mit durchschnittlicher Fahrzeit), Fahrzeug (mit Anzahl
  Sitzplätze), Route, Fahrgast/Kunde, Fahrer und Buchung/Fahrt.
- Die Route ist eine geordnete Liste von Haltepunkten. Modelliere zusätzlich,
  dass pro Haltepunkt auf der Route festgelegt ist, welche Fahrgäste dort
  aufgenommen und welche abgesetzt werden (Hinweis: dafür bietet sich eine
  eigene Klasse wie „Routenhalt" oder eine Assoziationsklasse an – begründe
  deine Wahl).
- Modelliere die Verbindung als ungerichtete Kante (keine Fahrtrichtung).
- Notiere die Kapazitätsregel (Fahrgäste ≤ Sitzplätze) und die
  Zentrale-Regel (Start-/Endpunkt jeder Route, kein Ein-/Ausstieg) als
  UML-Constraints in geschweiften Klammern oder als Notiz am Modell.
- Versieh alle Assoziationen mit Multiplizitäten; bei der geordneten Liste
  der Haltepunkte einer Route verwende {ordered}.
- Ergänze zentrale Methoden, mindestens für: Fahrt buchen, Wartezeit
  berechnen, Restfahrzeit berechnen, nächsten Haltepunkt abfragen, Ankunft
  bestätigen.

Prüfe vor der Ausgabe: Hat jede Assoziation Multiplizitäten? Ist die
Reihenfolge der Haltepunkte auf der Route erkennbar ({ordered})? Sind beide
Fachregeln als Constraint oder Notiz sichtbar?
```

**Begründung:**

- **Der „Routenhalt"-Hinweis ist die wichtigste Zeile des Prompts.** Die Anforderung „pro Haltepunkt auf der Route ist festgelegt, welche Fahrgäste dort ein-/aussteigen" ist eine dreistellige Beziehung (Route × Haltepunkt × Fahrgast) und damit die schwerste Modellierungsstelle aller drei Lastenhefte. Ohne Hinweis modellieren KIs meist nur Route→Haltepunkte und verlieren die Ein-/Ausstiegsinformation. Der Prompt nennt die zwei üblichen Lösungsmuster (Zwischenklasse, Assoziationsklasse), erzwingt aber keine davon – die KI muss ihre Wahl begründen, was wieder Präsentationsstoff liefert.
- **`{ordered}` explizit gefordert:** Dass die Haltepunktliste *geordnet* ist, ist fachlich essenziell (die Reihenfolge IST die Route) und wird in UML mit dem Standard-Constraint `{ordered}` notiert – ein Detail, das KIs ohne Aufforderung fast nie setzen, das aber in einer OOSE-Übung positiv auffällt.
- **Invarianten als Constraints/Notizen:** Die Kapazitäts- und Zentrale-Regel sind statisch nicht als Assoziation darstellbar. Die Notation als `{Constraint}` oder Notiz ist der UML-konforme Weg, sie trotzdem im Klassendiagramm zu dokumentieren – so geht die wichtigste Geschäftsregel des Systems nicht verloren.
- **Ungerichtete Kante betont:** KIs modellieren Graphkanten reflexhaft mit Richtung (von→nach). Das Lastenheft sagt ausdrücklich „ungerichteter Graph, Einbahnstraßen gibt es nicht".

### 4.3 Prompt: Use-Case-Diagramm

```text
Erstelle ein UML-Use-Case-Diagramm für EasyRide als PlantUML-Code mit
mindestens 5 Use Cases.

Anforderungen:
- Akteure: Kunde (Fahrgast) und Fahrer.
- Zeichne eine Systemgrenze mit dem Namen „EasyRide"; die Akteure stehen
  außerhalb.
- Die Systembeschreibung nennt die Leistungen für Kunden und Fahrer
  abschließend in zwei Listen. Leite die Use Cases genau daraus ab:
  Kunde: Fahrt buchen, Wartezeit abfragen (vor Fahrtantritt), Restfahrzeit
  abfragen (nach Fahrtantritt).
  Fahrer: Nächsten Haltepunkt mit Fahrgastwechsel abfragen, Erreichen eines
  Haltepunkts bestätigen.
- Verwende <<include>> oder <<extend>> nur, wenn es fachlich klar begründbar
  ist, und erkläre jede Verwendung. Im Zweifel lieber weglassen.
- Wenn du weitere Use Cases für sinnvoll hältst (z. B. interne
  Routenplanung), diskutiere in deiner Erläuterung, warum sie (nicht) ins
  Diagramm gehören.

Prüfe vor der Ausgabe: Sind es mindestens 5 Use Cases? Stehen beide Akteure
außerhalb der Systemgrenze? Ist jeder Use Case aus Akteurssicht formuliert
(Verb + Objekt)?
```

**Begründung:**

- **Hier ist die Kandidatenliste abschließend, nicht offen („u. a.") wie bei EasyScoot.** EasyRide nennt die Systemleistungen als exakt fünf Spiegelstriche in zwei „Zusammenfassend..."-Listen – das Lastenheft liefert die Use Cases also selbst, und genau fünf reichen für die Mindestanforderung. Jede Erfindung darüber hinaus (Konto anlegen, bezahlen, stornieren) wäre nicht belegbar. Der Prompt nutzt die Struktur des Lastenhefts als Autorität.
- **Diskussionsauftrag zur Routenplanung:** Die Routenplanung (neue Route anlegen / bestehende erweitern) ist zentrale Systemfunktion, aber *kein* Use Case eines menschlichen Akteurs – sie wird durch „Fahrt buchen" ausgelöst. Das ist die didaktisch interessanteste Falle dieses Lastenhefts: Wer „Route planen" als eigenen Use Case mit Akteur einzeichnet, hat das Akteurskonzept missverstanden. Der Prompt zwingt die KI, diese Abgrenzung explizit zu diskutieren, statt sie stillschweigend richtig oder falsch zu machen.
- **Keine Sekundärakteure gefordert:** Anders als EasyScoot hat EasyRide keine externen Systeme – Tablet und Smartphone sind nur Endgeräte der Akteure, keine eigenständigen Systeme. Sie als Akteure zu modellieren wäre ein Fehler; deshalb schweigt der Prompt hier bewusst, statt (wie bei EasyScoot) Sekundärakteure zu verlangen.

### 4.4 Prompt: Aktivitätsdiagramm

```text
Erstelle ein UML-Aktivitätsdiagramm für EasyRide als PlantUML-Code für das
Szenario „Kunde bucht eine Fahrt" – von der Eingabe von Start- und
Zielhaltepunkt bis zur Mitteilung der Wartezeit.

Anforderungen:
- Mindestens 5 Aktivitäten.
- Enthalten sein müssen mindestens: Start- und Zielhaltepunkt erfassen,
  passendes Fahrzeug/Route suchen, Kapazität prüfen, Route erweitern ODER
  neue Route anlegen, Fahrgast auf Routenhalte einplanen, Wartezeit berechnen
  und mitteilen.
- Mindestens zwei Entscheidungen mit beschrifteten Kanten, darunter:
  „Existierende Route erweiterbar (Kapazität und Strecke passend)?" mit den
  Ausgängen zu „Route erweitern" bzw. „neue Route anlegen".
- Verwende Swimlanes für Kunde und EasyRide-System.
- Beginne mit einem Startknoten und ende mit einem Endknoten.

Prüfe vor der Ausgabe: Sind es mindestens 5 Aktivitäten? Bildet eine
Entscheidung die Alternative „Route erweitern / neue Route anlegen" aus der
Systembeschreibung ab? Wird die Kapazitätsregel geprüft, bevor eine Route erweitert
wird?
```

**Begründung:**

- **Szenariowahl:** Die Buchung ist der einzige Prozess des Lastenhefts mit echter Verzweigungslogik – das Lastenheft selbst formuliert die Alternative „neue Route angelegt **oder** eine existierende Route verändert oder erweitert". Ein Aktivitätsdiagramm lebt von Entscheidungen; die Fahrer-Abläufe (Haltepunkt bestätigen) wären dagegen fast linear und würden die 5 Aktivitäten nur künstlich erreichen.
- **Die Entscheidung ist wörtlich vorgegeben,** weil sie die Kernaussage des Diagramms ist: Genau hier zeigt sich, ob der Ablauf das Lastenheft abbildet oder generisches „Fahrt buchen"-Wissen. Die Kapazitätsprüfung *vor* der Routenerweiterung ist die Verhaltensseite der Invariante aus dem Basis-Prompt (Regel 7b) – der Selbstprüfungs-Punkt kontrolliert genau diese Reihenfolge.
- **Zwei Entscheidungen gefordert (statt einer wie bei EasyScoot):** Neben der Routen-Alternative braucht der Ablauf realistisch eine zweite Verzweigung (z. B. „überhaupt ein Fahrzeug mit freier Kapazität gefunden?"). Das hebt das Diagramm über die Minimalversion und deckt den Fehlerfall ab, den das Lastenheft offenlässt – ein guter Kandidat für die Annahmenliste.

### 4.5 Prompt: Sequenzdiagramm

```text
Erstelle ein UML-Sequenzdiagramm für EasyRide als PlantUML-Code für das
Szenario „Fahrer bestätigt das Erreichen eines Haltepunkts".

Anforderungen:
- Mindestens 5 Methodenaufrufe.
- Beteiligte Lebenslinien: Fahrer (Akteur, via Tablet), das EasyRide-System,
  die aktuelle Route sowie die Buchung/Fahrt der betroffenen Fahrgäste.
- Der Ablauf muss fachlich zur Systembeschreibung passen: Ankunft am Haltepunkt
  bestätigen → Routenfortschritt aktualisieren → aufzunehmende und
  abzusetzende Fahrgäste am nächsten Haltepunkt ermitteln → verbleibende
  Fahrzeiten der betroffenen Fahrgäste aktualisieren → nächsten Haltepunkt
  mit Fahrgastnamen an das Tablet zurückgeben.
- Verwende synchrone Aufrufe mit Antwortpfeilen und sinnvolle
  Methodensignaturen mit Parametern.
- Nutze dieselben Klassen- und Methodennamen wie im Klassendiagramm aus
  dieser Konversation; ergänze fehlende Methoden dort gedanklich und weise
  darauf hin.

Prüfe vor der Ausgabe: Sind es mindestens 5 Methodenaufrufe? Hat jeder
synchrone Aufruf eine Antwort? Stimmen die Namen mit dem Klassendiagramm
überein?
```

**Begründung:**

- **Szenariowahl „Haltepunkt bestätigen" statt „Fahrt buchen":** Die Buchung ist bereits Gegenstand des Aktivitätsdiagramms – zwei Diagramme über denselben Ablauf wären redundant. Die Haltepunkt-Bestätigung ist der zweite fachliche Kernablauf und deckt die komplette Fahrer-Seite des Lastenhefts ab; zusammen zeigen Aktivitäts- und Sequenzdiagramm so *beide* Akteursperspektiven. Außerdem verknüpft dieses Szenario elegant beide Fahrer-Use-Cases (bestätigen + nächsten Halt abfragen) und die Kunden-Anforderung „Restfahrzeit in Abhängigkeit vom letzten erreichten Haltepunkt" – die Bestätigung ist genau das Ereignis, das die Restfahrzeit neu berechnet. Diese Querverbindung macht das Diagramm inhaltlich reich genug für ≥ 5 echte Aufrufe.
- **Route und Buchung als eigene Lebenslinien:** Zwingt die KI, die Objektstruktur aus dem Klassendiagramm wiederzuverwenden (Route kennt Halte und Fahrgastwechsel, Buchung kennt Start/Ziel des einzelnen Fahrgasts), statt alles in einer „System"-Lebenslinie zu verstecken – sonst bestünde das Diagramm aus zwei Pfeilen und erfüllte die Mindestzahl nicht sinnvoll.

---

<a id="easylib"></a>
## 5. EasyLib – Prompts und Begründungen

**Systemkontext:** Bestands- und Ausleihemanagement einer Bücherei (Ablösung einer Altsoftware). Akteure: Bibliothekar, Kunde, Buchhalter; externe Schnittstellen: zentraler Verbundkatalog und vernetzte Bibliotheken der Region. Fachlicher Kern des Datenmodells ist die Unterscheidung **Buch / Hörbuch / Exemplar**.

> **Hinweis zur Quelle:** Anders als EasyScoot und EasyRide liegt EasyLib nicht als eigenständiges PDF vor, sondern als „Lastenheft"-Folien in Kapitel 4 der Vorlesung (Folien 180–183). Die Systembeschreibung im Basis-Prompt fasst den Inhalt dieser vier Folien in eigenen Worten zusammen.

### 5.1 Basis-Prompt (zuerst senden)

```text
Du bist ein erfahrener Softwareanalytiker und UML-Modellierer. Wir analysieren
gemeinsam das Lastenheft „EasyLib" aus einem Hochschulkurs zur
objektorientierten Softwaretechnik und erstellen daraus schrittweise
UML-Diagramme (Klassendiagramm, Use-Case-Diagramm, Aktivitätsdiagramm,
Sequenzdiagramm).

Regeln für die gesamte Konversation:
1. Verwende ausschließlich Inhalte aus der folgenden Systembeschreibung; sie
   gibt das Lastenheft vollständig in eigenen Worten wieder. Erfinde keine
   zusätzlichen Features (z. B. keine Online-Ausleihe von E-Books, keine
   Gebührenzahlung, kein Empfehlungssystem).
2. Alle Bezeichner (Klassen, Attribute, Methoden, Use Cases, Aktivitäten) sind
   auf Deutsch.
3. Gib jedes Diagramm als PlantUML-Code in einem Codeblock aus, gefolgt von
   einer kurzen Erläuterung deiner Modellierungsentscheidungen.
4. Verwende korrekte UML-2-Notation.
5. Liste am Ende jeder Antwort deine Annahmen und erkannte Unklarheiten in
   den Anforderungen auf. Gehe dabei insbesondere auf die unten markierte
   Mehrdeutigkeit bei der Leihfristverlängerung ein: Benenne sie und triff
   eine begründete Annahme, statt sie stillschweigend zu übergehen.
6. Achte darauf, dass alle Diagramme zueinander konsistent sind: gleiche
   Klassen-, Akteurs- und Methodennamen über alle Diagramme hinweg.
7. Unterscheide durchgehend sauber zwischen einem Werk (Buch bzw. Hörbuch mit
   bibliografischen Daten) und seinen physischen Exemplaren (mit ID und
   Standort). Ausgeliehen und reserviert wird auf der fachlich jeweils
   richtigen Ebene – lege dich fest und begründe es.

Bestätige kurz, dass du die Systembeschreibung gelesen hast, und nenne die Akteure,
die externen Systeme und die zentralen Fachbegriffe. Erstelle noch kein
Diagramm.

---
SYSTEMBESCHREIBUNG „EasyLib" (Inhalt des Lastenhefts in eigenen Worten):

EasyLib ist die neu zu entwickelnde Software für das Bestands- und
Ausleihemanagement einer Bücherei; sie löst eine veraltete Altsoftware ab.

Funktionen für Bibliothekare:
- Exemplare in den Bestand einpflegen und wieder auspflegen; beim Einpflegen
  können die Buchdaten wahlweise aus dem zentralen Verbundkatalog importiert
  werden, statt sie manuell einzugeben
- Exemplare an Kunden verleihen und Rückgaben entgegennehmen
- den eigenen Bestand einsehen und nach Merkmalen wie Titel, Autor oder
  Genre durchsuchen
- ebenso den Bestand anderer, vernetzter Bibliotheken der Region einsehen
  und durchsuchen
- Standort sowie Ausleihe- und Reservierungsstatus der Exemplare eines
  Buchs einsehen
- Kundendaten samt zugehörigen Ausleihen und Reservierungen einsehen

Funktionen für Kunden:
- ein Kundenkonto anlegen und es löschen, sofern keine Ausleihen mehr offen
  sind
- den Bestand einsehen und nach Titel, Autor oder Genre durchsuchen
- Standort sowie Ausleihe- und Reservierungsstatus der Exemplare eines
  Buchs einsehen – jedoch ohne Einblick in Daten anderer Kunden (etwa wer
  ein Exemplar gerade ausgeliehen hat)
- ein Buch reservieren und eine Reservierung stornieren
- eine Leihfrist verlängern. (Achtung, Mehrdeutigkeit im Original: Dort
  heißt es, verlängert werden könne, „soweit eine andere Reservierung
  vorliegt" – fachlich plausibel ist eher das Gegenteil, also eine
  Verlängerung nur, wenn KEINE andere Reservierung vorliegt. Triff hierzu
  eine begründete Annahme.)

Funktion für den Buchhalter:
- eine Übersicht aller Ausleihen mit überschrittener Leihfrist einsehen, als
  Grundlage für Mahnbescheide

Datenmodell:
- Ein Buch hat Titel, Verlag, Auflage, Erscheinungsdatum, ISBN-Nummer,
  Seitenzahl, ein Genre aus einer festen Liste (Roman, Fantasy, Horror,
  Humor, Krimi, Science Fiction, Biografie, Ratgeber, Sachbuch) und einen
  oder mehrere Autoren.
- Ein Autor hat Namen und Vornamen, optional zusätzlich Mittelnamen und
  einen Namenszusatz (z. B. akademischer Titel).
- Zu einem Buch kann es mehrere physische Buchexemplare geben; jedes
  Exemplar hat eine eindeutige ID und einen Standort, der aus Etage und
  Regalnummer besteht.
- Zusätzlich verleiht die Bücherei Hörbücher auf CD: Ein Hörbuch hat keine
  Seitenzahl, sondern eine Anzahl an Datenträgern (CDs) und eine Spiellänge
  in Minuten; auch von Hörbüchern kann es mehrere Exemplare geben.
- Von Kunden speichert das System Namen und Anschrift (Straße, Hausnummer,
  Postleitzahl, Ort) sowie eine eindeutige Kunden-ID, die zusammen mit
  einem Lichtbild auf dem Bibliotheksausweis abgedruckt ist.
---
```

**Begründung (projektspezifisch):**

- **Regel 7 (Werk vs. Exemplar) ist das EasyLib-Pendant zu den EasyRide-Invarianten.** Die Unterscheidung Buch↔Buchexemplar ist der didaktische Kern dieses Lastenhefts (deshalb widmet ihm der Folientext einen ganzen Absatz). Der klassische Anfängerfehler – „Kunde leiht Buch" statt „Kunde leiht Exemplar" – wird hier zentral adressiert. Bewusst offen gelassen ist, ob *Reservierungen* auf Buch- oder Exemplarebene liegen: Das Lastenheft sagt „ein Buch reservieren", zeigt aber auch einen „Reservierungsstatus von Exemplaren" – eine echte Mehrdeutigkeit, die die KI erkennen und begründet auflösen soll.
- **Die offen markierte Mehrdeutigkeit bei der Leihfristverlängerung:** Die Original-Folie formuliert, eine Leihfrist sei zu verlängern, „soweit eine andere Reservierung vorliegt" – fachlich ergibt nur das Gegenteil Sinn (Verlängerung, *sofern keine* andere Reservierung vorliegt); offenbar ein Formulierungsfehler. Da die Systembeschreibung in eigenen Worten verfasst ist, kann sie diese Stelle nicht unauffällig „mitschleppen": Sie stillschweigend zu korrigieren würde den Fehler verstecken (und die Abgabe wäre gegenüber dem Original nicht mehr nachvollziehbar), sie unkommentiert nachzubilden würde die KI in die Irre führen. Deshalb markiert die Beschreibung die Stelle offen als Unklarheit, zitiert nur die betroffene Kurzformulierung und verpflichtet die KI in Regel 5 zu einer begründeten Annahme. So landet der Punkt samt Interpretation in der Annahmenliste – ideales Material für die Übungsdiskussion, denn genau solche Lastenheft-Schwächen sind Thema von Kapitel 4.
- **Negativliste angepasst:** Bei Bibliothekssystemen ergänzen KIs typischerweise E-Book-Ausleihe, Mahngebühren-Bezahlung und Empfehlungen. Das Lastenheft endet aber beim *Einsehen* der überfälligen Ausleihen (der Mahnbescheid selbst ist Handarbeit des Buchhalters) – die Grenze wird explizit gezogen.

### 5.2 Prompt: Klassendiagramm

```text
Erstelle ein UML-Klassendiagramm für EasyLib als PlantUML-Code.

Anforderungen:
- Modelliere die Vererbungsstruktur des Bestands: Buch und Hörbuch haben
  gemeinsame bibliografische Merkmale (Titel, Verlag, Auflage,
  Erscheinungsdatum, ISBN, Genre, Autoren), unterscheiden sich aber: Buch hat
  eine Seitenzahl, Hörbuch stattdessen Anzahl Datenträger und Spiellänge in
  Minuten. Entscheide begründet, ob du eine gemeinsame (ggf. abstrakte)
  Oberklasse wie „Medium" einführst.
- Modelliere Exemplare getrennt von Werken: Ein Exemplar hat eine eindeutige
  ID und einen Standort (Etage, Regalnummer); zu einem Werk kann es mehrere
  Exemplare geben.
- Autor ist eine eigene Klasse (Name, Vorname, optional Mittelname und
  Namenszusatz); ein Werk hat einen oder mehrere Autoren (Multiplizität 1..*).
- Genre ist eine Enumeration mit genau den neun Werten aus der
  Systembeschreibung.
- Modelliere Kunde (Name, Anschrift: Straße, Hausnummer, PLZ, Ort;
  Kunden-ID, Lichtbild/Bibliotheksausweis), Ausleihe (mit Leihfrist) und
  Reservierung als eigene Klassen mit Assoziationen zu Kunde und
  Exemplar bzw. Werk (gemäß deiner Entscheidung aus dem Basis-Prompt).
- Bibliothekar und Buchhalter: Entscheide begründet, ob sie als Klassen ins
  Diagramm gehören oder nur Akteure des Use-Case-Diagramms sind.
- Deute die externen Systeme (Verbundkatalog, vernetzte Bibliotheken) als
  Schnittstellen an.
- Versieh alle Assoziationen mit Multiplizitäten.

Prüfe vor der Ausgabe: Ist die Vererbung Buch/Hörbuch korrekt (gemeinsame
Attribute nur in der Oberklasse)? Hängen Ausleihe und Reservierung an der
fachlich richtigen Ebene (Werk vs. Exemplar)? Hat die Autor-Assoziation die
Multiplizität 1..*?
```

**Begründung:**

- **EasyLib ist das datenmodell-lastigste der drei Lastenhefte** – zwei volle Absätze reine Attributbeschreibung. Entsprechend ist dieser Prompt der detaillierteste Klassendiagramm-Prompt: Er nennt die Attribute samt Verteilung auf Ober-/Unterklasse, weil die Generalisierung Buch/Hörbuch die zentrale Prüfstelle ist. Das Lastenheft formuliert sie nur implizit („im Gegensatz zum gedruckten Buch keine Seitenzahl, sondern …") – der Prompt übersetzt das in die Modellierungsfrage, lässt aber die Entscheidung über eine Oberklasse „Medium" (samt Name und Abstraktheit) bei der KI, damit eine begründete Designentscheidung entsteht.
- **„Genre mit genau den neun Werten":** Die Werteliste steht vollständig im Lastenheft. „Genau" verhindert sowohl Auslassungen als auch kreative Ergänzungen (KIs fügen gern „Thriller" hinzu). Ein mechanisch prüfbares Kriterium.
- **Bibliothekar/Buchhalter-Frage explizit gestellt:** Ob Systemnutzer als Klassen ins Fachmodell gehören, ist eine Standarddiskussion. Bei EasyScoot mussten sie hinein (das Lastenheft fordert Nutzerkonten mit Daten), bei EasyLib schweigt das Lastenheft über gespeicherte Bibliothekars-Daten – vermutlich gehören sie nur ins Use-Case-Diagramm. Die KI soll das erkennen; die unterschiedliche Behandlung in den zwei Projekten ist selbst ein Lehrstück.
- **Optionale Attribute (Mittelname, Namenszusatz):** Kleines, aber feines UML-Detail (Multiplizität [0..1] am Attribut) – im Prompt erwähnt, weil das Lastenheft „optional" ausdrücklich sagt.

### 5.3 Prompt: Use-Case-Diagramm

```text
Erstelle ein UML-Use-Case-Diagramm für EasyLib als PlantUML-Code mit
mindestens 5 Use Cases.

Anforderungen:
- Akteure: Bibliothekar, Kunde, Buchhalter sowie der Verbundkatalog und die
  vernetzten Bibliotheken als Sekundärakteure (externe Systeme), wo sie an
  Use Cases beteiligt sind.
- Zeichne eine Systemgrenze mit dem Namen „EasyLib"; alle Akteure stehen
  außerhalb.
- Leite die Use Cases aus den drei Nutzergruppen der Systembeschreibung ab,
  u. a.:
  Bibliothekar: Exemplar einpflegen, Exemplar auspflegen, Exemplar verleihen,
  Rückgabe entgegennehmen, Bestand durchsuchen, Bestand vernetzter
  Bibliotheken durchsuchen, Kundendaten einsehen.
  Kunde: Kundenkonto anlegen, Kundenkonto löschen, Bestand durchsuchen, Buch
  reservieren, Reservierung stornieren, Leihfrist verlängern.
  Buchhalter: Überfällige Ausleihen einsehen.
- Beachte: „Bestand durchsuchen" wird von Bibliothekar UND Kunde genutzt –
  modelliere das als einen Use Case mit zwei Akteuren, nicht doppelt.
- Prüfe, ob der Import aus dem Verbundkatalog als <<include>> oder <<extend>>
  von „Exemplar einpflegen" sinnvoll ist, entscheide dich begründet.
  Verwende include/extend sonst nur, wenn fachlich klar begründbar.

Prüfe vor der Ausgabe: Sind es mindestens 5 Use Cases? Teilen sich
Bibliothekar und Kunde den Use Case „Bestand durchsuchen"? Ist der
Verbundkatalog als Akteur mit dem Einpflegen verbunden?
```

**Begründung:**

- **Der Fall „geteilter Use Case" ist die EasyLib-Besonderheit:** Bestand durchsuchen kommt in beiden Aufzählungen des Lastenhefts fast wortgleich vor. KIs erzeugen daraus gern zwei getrennte Use Cases („Bestand durchsuchen (Bibliothekar)" / „Bestand durchsuchen (Kunde)") – Duplikation statt zwei Assoziationen an einem Use Case. Der Prompt untersagt das ausdrücklich, weil es die Kernidee des Use-Case-Diagramms (Leistung des Systems, nicht des Nutzers) betrifft.
- **Die include/extend-Frage ist hier bewusst NICHT gedrosselt, sondern gestellt:** Der Katalogimport ist der Lehrbuchfall für diese Diskussion – optionaler Bestandteil des Einpflegens („statt die Daten manuell einzugeben"), also gut als `<<extend>>` argumentierbar, aber auch als eingeschlossener Alternativweg diskutierbar. Anders als bei EasyScoot/EasyRide (wo es keine klaren Kandidaten gibt und Drosselung Fehler vermeidet) gibt es hier genau einen guten Kandidaten; die erzwungene Entscheidung samt Begründung ist wertvoller Präsentationsstoff.
- **Mehr als 5 Use Cases in der Kandidatenliste:** EasyLib hat die meisten Einzelanforderungen der drei Lastenhefte (14 Spiegelstriche). Die Liste nennt die wichtigsten und überlässt der KI die Auswahl/Bündelung – z. B. kann sie „einpflegen/auspflegen" als zwei Use Cases führen oder Standort-/Statusabfragen ergänzen. Die Mindestzahl 5 ist so in jedem Fall übererfüllt und das Diagramm bleibt trotzdem lesbar.

### 5.4 Prompt: Aktivitätsdiagramm

```text
Erstelle ein UML-Aktivitätsdiagramm für EasyLib als PlantUML-Code für das
Szenario „Bibliothekar pflegt ein neues Buchexemplar ein" – inklusive der
Entscheidung zwischen Katalogimport und manueller Eingabe.

Anforderungen:
- Mindestens 5 Aktivitäten.
- Enthalten sein müssen mindestens: ISBN bzw. Buchdaten erfassen,
  Verbundkatalog abfragen, Buchdaten importieren, Buchdaten manuell
  eingeben, prüfen ob das Werk bereits im Bestand existiert, Exemplar
  anlegen, Standort (Etage, Regalnummer) zuweisen.
- Mindestens zwei Entscheidungen mit beschrifteten Kanten:
  1) „Buchdaten im Verbundkatalog gefunden?" → importieren / manuell eingeben
  2) „Werk bereits im Bestand?" → nur neues Exemplar anlegen / Werk neu
     anlegen und Exemplar anlegen
- Verwende Swimlanes für Bibliothekar, EasyLib-System und Verbundkatalog.
- Beginne mit einem Startknoten und ende mit einem Endknoten.

Prüfe vor der Ausgabe: Sind es mindestens 5 Aktivitäten? Führen beide Zweige
der Import-Entscheidung wieder zusammen? Wird zwischen „Werk anlegen" und
„Exemplar anlegen" unterschieden?
```

**Begründung:**

- **Szenariowahl:** Das Einpflegen ist der einzige EasyLib-Prozess mit natürlicher Verzweigung, die das Lastenheft selbst nennt („importieren, **statt** die Daten manuell einzugeben") und mit externer Systembeteiligung (Verbundkatalog). Es ist zudem exakt das Beispiel, das die Vorlesung in Kapitel 4 selbst als Systemschnittstellen-Beispiel verwendet („Systemschnittstelle Buchexemplar einpflegen") – die Abgabe knüpft damit direkt an den Vorlesungsstoff an. Die Alternative „Buch ausleihen" wird bewusst für das Sequenzdiagramm aufgespart (Begründung dort).
- **Die zweite Entscheidung („Werk bereits im Bestand?") steht nicht wörtlich im Lastenheft,** folgt aber zwingend aus dem Datenmodell: Wenn es zu einem Buch mehrere Exemplare gibt, muss der Einpflege-Prozess unterscheiden, ob nur ein Exemplar oder auch das Werk neu anzulegen ist. Der Prompt gibt diese Entscheidung vor, weil sie das Verständnis der Werk/Exemplar-Trennung (Regel 7 des Basis-Prompts) auf der *Verhaltensebene* nachweist – und dokumentiert damit zugleich eine ableitbare, aber implizite Anforderung, die in die Annahmenliste gehört.
- **Zusammenführung der Zweige als Prüfpunkt:** Import und manuelle Eingabe münden in denselben Folgeprozess (Exemplar anlegen). KI-generierte Aktivitätsdiagramme lassen alternative Zweige oft getrennt ins Leere laufen – der Merge-Knoten ist der Notationstest dieses Diagramms.

### 5.5 Prompt: Sequenzdiagramm

```text
Erstelle ein UML-Sequenzdiagramm für EasyLib als PlantUML-Code für das
Szenario „Bibliothekar verleiht ein Buchexemplar an einen Kunden".

Anforderungen:
- Mindestens 5 Methodenaufrufe.
- Beteiligte Lebenslinien: Bibliothekar (Akteur), das EasyLib-System, der
  Kunde (als Objekt im System), das Buchexemplar und die neu entstehende
  Ausleihe.
- Der Ablauf muss fachlich zur Systembeschreibung passen: Kunde anhand der Kunden-ID
  vom Bibliotheksausweis ermitteln → Exemplar anhand seiner ID ermitteln →
  prüfen, ob das Exemplar verfügbar ist (nicht verliehen, keine
  entgegenstehende Reservierung) → Ausleihe mit Leihfrist anlegen →
  Ausleihe- und Reservierungsstatus des Exemplars aktualisieren →
  Bestätigung an den Bibliothekar.
- Zeige die Objekterzeugung der Ausleihe als create-Nachricht.
- Verwende synchrone Aufrufe mit Antwortpfeilen und sinnvolle
  Methodensignaturen mit Parametern.
- Nutze dieselben Klassen- und Methodennamen wie im Klassendiagramm aus
  dieser Konversation; ergänze fehlende Methoden dort gedanklich und weise
  darauf hin.

Prüfe vor der Ausgabe: Sind es mindestens 5 Methodenaufrufe? Wird die
Ausleihe per create-Nachricht erzeugt? Wird das Exemplar (nicht das Buch)
verliehen?
```

**Begründung:**

- **Szenariowahl „Exemplar verleihen":** Die Ausleihe ist der namensgebende Kernprozess des Systems („Ausleihemanagement") und der einzige, bei dem zur Laufzeit ein neues Fachobjekt entsteht – deshalb fordert der Prompt die **create-Nachricht**, ein Sequenzdiagramm-Element, das die anderen beiden Projekte nicht hergeben. So decken die drei Sequenzdiagramme zusammen unterschiedliche Notationselemente ab (EasyScoot: externes System, EasyRide: mehrere Fachobjekt-Lebenslinien, EasyLib: Objekterzeugung).
- **Verfügbarkeitsprüfung im Ablauf verankert:** Sie verbindet das Sequenzdiagramm mit dem Reservierungskonzept aus dem Klassendiagramm und erzwingt Aufrufe an der Exemplar-Lebenslinie – ohne sie würde die KI den gesamten Vorgang in einer einzigen „System"-Methode kapseln und die Mindestzahl nur formal erfüllen.
- **Letzter Prüfpunkt „Exemplar, nicht Buch":** Die Werk/Exemplar-Regel aus dem Basis-Prompt wird hier ein drittes Mal kontrolliert – bewusste Redundanz, weil dieser Fehler in Abgaben zum EasyLib-Beispiel erfahrungsgemäß am häufigsten vorkommt und sich durch alle Diagramme zieht, wenn er einmal drin ist.

---

<a id="qualitaet"></a>
## 6. Qualitätskontrolle der KI-Ergebnisse

Die Prompts minimieren Fehler, garantieren aber keine fehlerfreien Diagramme – KI-Ausgaben sind nicht deterministisch. Vor der Abgabe sollte jedes Diagramm gegen diese Checkliste geprüft werden:

**Alle Diagramme:**

- Kommt jedes Modellelement im Lastenheft vor (rückwärts prüfbar: zu jedem Element die Textstelle suchen)?
- Sind die Mindestzahlen erfüllt (nachzählen: ≥ 5 Use Cases / Aktivitäten / Methodenaufrufe)?
- Sind alle Bezeichner deutsch und über die Diagramme hinweg identisch?

**Klassendiagramm:** Multiplizitäten an jeder Assoziation; Enumerationen statt String-Attribute für feste Wertelisten; externe Systeme als Schnittstelle, nicht als Fachklasse.

**Use-Case-Diagramm:** Akteure außerhalb der Systemgrenze; Use Cases als Verb + Objekt; jedes include/extend begründet und richtig herum (die Pfeilrichtung von include und extend ist entgegengesetzt – häufiger KI-Fehler).

**Aktivitätsdiagramm:** Start- und Endknoten vorhanden; jede Entscheidungsraute mit beschrifteten Ausgängen; alternative Zweige wieder zusammengeführt; Aktivitäten in der richtigen Swimlane.

**Sequenzdiagramm:** Jeder synchrone Aufruf (gefüllte Pfeilspitze) mit gestrichelter Antwort; Methoden stehen an der Lebenslinie des *Empfängers*; alle Methoden existieren im (ggf. nachgezogenen) Klassendiagramm.

**Empfohlener Umgang mit Fehlern:** Nicht neu generieren lassen, sondern gezielt korrigieren („Ergänze die Multiplizität zwischen Route und Haltepunkt") – Neugenerierung wirft oft korrekte Teile wieder um. Wenn die KI in ihrer Annahmenliste Unklarheiten nennt, diese für die Präsentation notieren: Sie sind Diskussionsbeitrag, kein Makel.

---

*Erstellt am 06.07.2026 auf Basis der Lastenhefte „EasyScoot" und „EasyRide" (B-Übung, PDF) sowie des EasyLib-Lastenhefts aus Kapitel 4 (Folien 180–183), OOSE-I Q3 2025.*
