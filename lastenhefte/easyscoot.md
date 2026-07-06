Objektorientierte Softwaretechnik I

Q3 2025

Lastenheft „EasyScoot“

Es soll eine neue Software für einen E-Scooter-Verleih entwickelt werden. In einer Stadt sind an
bestimmten Orten E-Scooter verteilt. Diese sollen von Kunden per Smartphone gebucht und
freigeschaltet, benutzt und letztlich an einem beliebigen Zielort wieder abgestellt werden
können.

Für die E-Scooter wurde bereits eine Software entwickelt, die per Mobilfunk verbunden ist und in
regelmäßigen Abständen Position, Ladezustand und Fahrstatus (stehend, fahrend) an
EasyScoot sendet.

Möchte ein Kunde einen E-Scooter nutzen, muss er zunächst ein EasyScoot-Kundenkonto
erstellen, wo Vorname, Name, Anschrift (Straße, Hausnummer, PLZ, Ort) und Emailadresse
gespeichert wird. Dann kann der Kunde abfragen, welche E-Scooter sich in seiner Nähe
befinden, und bekommt eine Liste von freien E-Scootern mit Standorten und Ladestand und
geschätzter übriger Fahrzeit in Minuten angezeigt. Der E-Scooter speichert Marke, Modell, die
Batteriekapazität (in Wattstunden) und den durchschnittlichen Verbrauchskoeffizienten
(Verbrauch in Wattstunden pro Kilometer).

Hat der Kunde einen E-Scooter in seiner Nähe gefunden, kann er sich zum Standort des E-
Scooters begeben. Ist der Kunde dort angekommen, kann er den E-Scooter buchen und
freischalten.

Ist der E-Scooter freigeschaltet, kann der Kunde ihn nutzen. Am Zielort angekommen, beendet
der Kunde die Benutzung via Smartphone. Daraufhin bekommt der Kunde eine
Zusammenfassung der Fahrt angezeigt (Dauer, gefahrene Kilometer, verbrauchte Wattstunden,
Preis). Die Berechnung des Preises geschieht durch ein existierendes Rechnungssystem, das an
EasyScoot angebunden werden soll.

Zu den weiteren Nutzern von EasyScoot gehören Flottenmanager und Service-Mitarbeiter, die
über entsprechende Nutzerkonten verfügen.

Ein Flottenmanager soll jederzeit eine Liste aller E-Scooter mit allen Informationen einsehen
können. Das sind: ID, Position, Ladestand, geschätzte übrige Fahrzeit, Fahrstatus (stehend,
fahrend), Leihstatus (in Benutzung oder nicht), Wartungsstatus (In Wartung / nicht in Wartung).

Service-Mitarbeiter sollen auch eine Liste aller E-Scooter einsehen können und speziell auch
eine gefilterte Liste mit allen E-Scooter, die einen Ladestand von 50% oder weniger haben.
Service-Mitarbeiter können E-Scooter mit geringer Kapazität zu Ladestationen bringen. Für den
Transport und den Ladevorgang schalten Service-Mitarbeiter die E-Scooter in einen
Wartungsmodus. Dabei wird der E-Scooter per Mobilfunk abgemeldet und in EasyScoot soll für
den E-Scooter der Wartungsstatus auf „in Wartung“ gesetzt werden. Beendet ein Service-
Mitarbeiter den Wartungsstatus, meldet sich der E-Scooter per Mobilfunk an und in EasyScoot
soll der Wartungsstatus auf „nicht in Wartung“ gesetzt werden.

Service-Mitarbeiter sollen zudem in der Lage sein, neue E-Scooter in die Flotte aufzunehmen
oder auszumustern.

