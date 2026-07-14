# Prompt: sequenz – easyscoot v1

Systemspezifischer Prompt, übernommen aus `dokumentation/quelle-ki-prompts-oose1.md`
(Abschnitte 3.1 und 3.5, dort auch die ausführlichen Begründungen).
Einzige Änderung gegenüber der Quelle: Beide Ausgabeformen (direkt gezeichnetes Bild und
PlantUML-Code) werden explizit gefordert – gemäß Aufgabenstellung und `prompts/README.md`.

**Verwendung:** Frische Chat-Session. Schritt 1 senden und die Bestätigung der KI abwarten
(Verständnis-Check), dann Schritt 2 senden.

## Schritt 1: Basis-Prompt

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
3. Gib jedes Diagramm in zwei Formen aus: (a) als von dir direkt
   gezeichnetes/generiertes Diagrammbild und (b) als PlantUML-Code in einem
   Codeblock. Ergänze jeweils eine
   kurze Erläuterung deiner Modellierungsentscheidungen.
4. Verwende korrekte UML-2-Notation.
5. Liste am Ende jeder Antwort deine Annahmen und erkannte Unklarheiten in
   den Anforderungen auf.
6. Achte darauf, dass alle Diagramme zueinander konsistent sind: gleiche
   Klassen-, Akteurs- und Methodennamen über alle Diagramme hinweg.

Bestätige kurz, dass du die Systembeschreibung gelesen hast, und nenne die Akteure und
externen Systeme, die du erkennst. Erstelle noch kein Diagramm.

---
SYSTEMBESCHREIBUNG „EasyScoot":

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

## Schritt 2: Diagramm-Prompt

```text
Erstelle ein UML-Sequenzdiagramm für EasyScoot für das Szenario „Kunde
beendet die Nutzung eines E-Scooters". Liefere es in beiden Formen: als
direkt gezeichnetes Diagrammbild und als PlantUML-Code.

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
