# Prompt: use-case – easyride v1

Systemspezifischer Prompt, übernommen aus `dokumentation/quelle-ki-prompts-oose1.md`
(Abschnitte 4.1 und 4.3, dort auch die ausführlichen Begründungen).
Einzige Änderung gegenüber der Quelle: Beide Ausgabeformen (direkt gezeichnetes Bild und
PlantUML-Code) werden explizit gefordert – gemäß Aufgabenstellung und `prompts/README.md`.

**Verwendung:** Frische Chat-Session. Schritt 1 senden und die Bestätigung der KI abwarten
(Verständnis-Check), dann Schritt 2 senden.

## Schritt 1: Basis-Prompt

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
3. Gib jedes Diagramm in zwei Formen aus: (a) als von dir direkt
   gezeichnetes/generiertes Diagrammbild und (b) als PlantUML-Code in einem
   Codeblock; beide müssen inhaltlich übereinstimmen. Ergänze jeweils eine
   kurze Erläuterung deiner Modellierungsentscheidungen.
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
SYSTEMBESCHREIBUNG „EasyRide":

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

## Schritt 2: Diagramm-Prompt

```text
Erstelle ein UML-Use-Case-Diagramm für EasyRide mit mindestens 5 Use Cases.
Liefere es in beiden Formen: als direkt gezeichnetes Diagrammbild und als
PlantUML-Code.

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
