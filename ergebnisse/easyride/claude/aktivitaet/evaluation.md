# Evaluation: easyride / claude / aktivitaet

| | |
|---|---|
| Bewertet von | Claude (Cowork) – vorlaeufige Selbstbewertung, unabhaengige Pruefung durch Teammitglied ausstehend |
| Datum | 2026-07-06 |
| Artefakt-Version | v1 |
| Verwendeter Prompt | `prompts/aktivitaet/easyride-v1.md` |
| Rendering-Weg | ausstehend – in dieser Session kein PlantUML-Rendering moeglich |

Skalen und Regeln: `evaluation/kriterien.md`. Jeder Score braucht Befunde.

## K1 – Syntaktische Korrektheit — Score: offen (Rendering ausstehend)

- PlantUML kompiliert ohne Korrektur: noch nicht geprueft – kein Renderlauf moeglich
  (plantuml.jar-Download blockiert, HTTP 403). Im Team-Renderweg pruefen, Ergebnis eintragen.
- Struktur-Vorpruefung (ersetzt kein Rendering): @startuml/@enduml paarig, 2x if/else/endif
  paarig (verschachtelt), 2 Swimlanes, genau ein start und ein stop, alle Aktionen als :...;
- Direktes Bild – UML-Notation korrekt?: v1-direkt.png ergaenzt (2026-07-06). Sichtpruefung: korrekte Aktivitaetsdiagramm-Notation (Start-/Endknoten, Aktionen, Rauten-Entscheidungen mit beschrifteten Kanten, Swimlanes). Formale Bewertung durch Teammitglied ausstehend.

## K2 – Inhaltliche Korrektheit — Score: 5 (vorlaeufig)

Abgleich mit `lastenhefte/easyride.md`, konkrete Befunde:

- Kernablauf getroffen: Buchung fuehrt zu "neue Route anlegen" ODER "existierende Route
  erweitern" (Lastenheft: "neue Route angelegt oder eine existierende Route veraendert
  oder erweitert"). ✓
- Kapazitaetsregel abgebildet: Pruefung von Kapazitaet/Strecke als eigene Aktion VOR der
  Erweiterungs-Entscheidung (Fachregel: nie mehr Fahrgaeste als Sitzplaetze). ✓
- Zentrale-Regel abgebildet: neue Route "Beginn und Ende an der Zentrale". ✓
- Routensemantik korrekt: Fahrgast wird auf Routenhalte eingeplant (Zustieg am Start,
  Ausstieg am Ziel) – entspricht "pro Haltepunkt: wer steigt zu/aus". ✓
- Wartezeit korrekt definiert: Zeit bis zum Erreichen des Starthaltepunkts. ✓
- Keine erfundenen Features (keine Bezahlung, Bewertung, kein Tracking). ✓
- Anmerkungen (keine Fehler): "Route veraendern" aus dem Lastenheft ist nicht als eigener
  dritter Fall modelliert – der Prompt gibt nur die Alternative erweitern / neu anlegen vor.
  "Buchung bestaetigen" ist generischer Interaktionsabschluss ohne Lastenheft-Wortlaut.

## K3 – Vollstaendigkeit — Score: 5 (vorlaeufig)

- Mindestanforderung erfuellt (Aktivitaeten >= 5): ja – 11 Aktionen.
- Alle geforderten Pflicht-Aktivitaeten enthalten (Start/Ziel erfassen, Fahrzeug/Route
  suchen, Kapazitaet pruefen, Route erweitern ODER neue Route anlegen, Fahrgast auf
  Routenhalte einplanen, Wartezeit berechnen und mitteilen); 2 Entscheidungen mit
  beschrifteten Kanten, darunter die geforderte Erweiterbarkeits-Entscheidung;
  Swimlanes Kunde/EasyRide-System; Start- und Endknoten.
- Fehlende zentrale Elemente: keine fuer das geforderte Szenario. Peripher, vom Szenario
  nicht verlangt: Ablehnungs-/Fehlerpfade (kein Fahrzeug verfuegbar), Fall "Route
  veraendern", uebrige Fahrzeit nach Fahrtantritt (anderes Szenario).

## K4 – Lesbarkeit / Zeichenqualitaet

- PlantUML-Rendering — Score: offen, Befunde: noch nicht gerendert.
- Direktes Bild — Score: 5 (vorlaeufig), Befunde: v1-direkt.png sauber lesbar – klare Swimlanes, keine Ueberlappungen, beschriftete Kanten; unabhaengige Bestaetigung ausstehend.

## PlantUML vs. direkt – Unterschiede

- Noch nicht bewertbar: nur PlantUML-Form vorhanden, kein direktes Bild, kein Rendering.

## Was haetten wir anders modelliert?

- Duplizierten Knoten "Neue Route anlegen" vermeiden, z. B. durch kombinierte Entscheidung
  oder explizite Zusammenfuehrung (Merge-Knoten) vor dem Anlegen.
- Ablehnungspfad ergaenzen (kein Fahrzeug mit freier Kapazitaet verfuegbar -> Buchung
  nicht moeglich) inkl. Mitteilung an den Kunden.
- "Route veraendern" (Umplanung bestehender Halte) als dritten Ausgang abbilden.
- Objektfluss ("Buchungsanfrage", "Route" als Objektknoten) fuer praezisere UML-Semantik.

## Sonstige Beobachtungen

- Methodik-Abweichungen (gleiche Session wie easylib-Aktivitaetsdiagramm unmittelbar zuvor
  -> moeglicher Struktur-Uebertrag zwischen Systemen; nur PlantUML-Form; kein Rendering) –
  Details in `notizen.md`.
