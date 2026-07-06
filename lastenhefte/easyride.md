Objektorientierte Softwaretechnik I

Q3 2025

Lastenheft „EasyRide“

Es soll eine Software für ein Ridesharing-System in einer Stadt entwickelt werden. In der Stadt
fährt eine Flotte von Fahrzeugen und transportiert Fahrgäste innerhalb eines Netzes von
Haltepunkten. Dabei kann ein Fahrzeug auch mehrere Fahrgäste mit unterschiedlichen Start-
und Zielhaltepunkten aufnehmen.

Fahrzeuge dürfen nur an definierten Haltepunkten halten. Das Netz aus Haltepunkten und den
Verbindungen zwischen ihnen ist ein ungerichteter Graph. Einbahnstraßen gibt es nicht. Für
jede direkte Verbindung zwischen Haltepunkten ist eine durchschnittliche Fahrzeit hinterlegt.

Die Flotte besteht aus mehreren Fahrzeugen, die sich in der Anzahl Sitzplätze unterscheiden.

Buchen Kunden eine Fahrt, so soll für ein Fahrzeug eine neue Route angelegt oder eine
existierende Route verändert oder erweitert werden. Eine Route ist eine Liste von Haltepunkten,
die das Fahrzeug nacheinander besuchen soll, um Fahrgäste aufzunehmen und abzusetzen.
Jede Route beginnt und endet an einem Haltepunkt „Zentrale“, der nicht zum Ein- und
Aussteigen genutzt werden kann.
Die Route beschreibt zudem pro Haltepunkt auf der Route, welche Fahrgäste dort
aufgenommen oder abgesetzt werden sollen. Eine Route darf nie so gestaltet sein, dass die
Anzahl an Fahrgästen die Anzahl an Sitzplätzen im Fahrzeug übersteigt.

Fahrzeuge werden von Fahrern gesteuert, die über ein Tablet bestätigen sollen, wenn ein
Haltepunkt erreicht wurde. Über das Tablet sollen die Fahrer zudem den nächsten
anzufahrenden Haltepunkt abfragen können sowie die Namen der dort aufzunehmenden und
abzusetzenden Fahrgäste.

Zusammenfassend soll es das zu entwickelnde Softwaresystem Kunden z.B. per Smartphone
ermöglichen:

•  Eine Fahrt von einem Start- zu einem Zielort zu buchen
•

vor Fahrtantritt zu erfahren, wie lange die übrige Wartezeit ist (d.h., die Zeit, bis das
Fahrzeug am gewählten Startpunkt ist)

•  nach Fahrtantritt zu erfahren, wie lange die übrige Fahrzeit bis zum Zielort ist (d.h., die

verbleibende Zeit in Abhängigkeit vom letzten erreichten Haltepunkt)

Das zu entwickelnde Softwaresystem soll es Fahrern ermöglichen:

•  den nächsten anzufahrenden Haltepunkt abzufragen, sowie die Namen der dort

aufzunehmenden und abzusetzenden Fahrgäste
•  das Erreichen des nächsten Haltepunkts zu bestätigen

