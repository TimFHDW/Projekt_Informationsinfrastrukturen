# Prompt: use-case – easylib v1

Systemspezifischer Prompt, übernommen aus `dokumentation/quelle-ki-prompts-oose1.md`
(Abschnitte 5.1 und 5.3, dort auch die ausführlichen Begründungen).
Einzige Änderung gegenüber der Quelle: Beide Ausgabeformen (direkt gezeichnetes Bild und
PlantUML-Code) werden explizit gefordert – gemäß Aufgabenstellung und `prompts/README.md`.

Hinweis zur Quelle: EasyLib liegt nicht als eigenständiges PDF vor, sondern als
Lastenheft-Folien in Kapitel 4 der Vorlesung (Folien 180–183); die Systembeschreibung in
Schritt 1 fasst diese Folien in eigenen Worten zusammen.

**Verwendung:** Frische Chat-Session. Schritt 1 senden und die Bestätigung der KI abwarten
(Verständnis-Check), dann Schritt 2 senden.

## Schritt 1: Basis-Prompt

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
3. Gib jedes Diagramm in zwei Formen aus: (a) als von dir direkt
   gezeichnetes/generiertes Diagrammbild und (b) als PlantUML-Code in einem
   Codeblock. Ergänze jeweils eine
   kurze Erläuterung deiner Modellierungsentscheidungen.
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
SYSTEMBESCHREIBUNG „EasyLib":

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

## Schritt 2: Diagramm-Prompt

```text
Erstelle ein UML-Use-Case-Diagramm für EasyLib mit mindestens 5 Use Cases.
Liefere es in beiden Formen: als direkt gezeichnetes Diagrammbild und als
PlantUML-Code.

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
