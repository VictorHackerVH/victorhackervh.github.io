Alle Zusammenfassungen: [[Überblick Zusammenfassungen]]

Letztes Kapitel: [[Kapitel 6 - Vererbung]]
# Lernziele
- Sie können die wesentlichen Eigenschaften von Interfaces beschreiben.
- Sie können Interfaces deklarieren und implementieren.
- Sie können Interfaces vererben.
- Sie können Interfaces in der UML darstellen.
- Sie kennen die besondere Bedeutung von Interfaces in Bezug auf Mehrfachvererbung.
- Sie können Polymorphie mit Hilfe von Interfaces realisieren.
- Sie können Objekte kopieren

# Zusammenfassung
## Eigenschaften von Interfaces
- Sind eine besondere Form von Klassen
- sie definieren lediglich den Aufbau der Schnittstelle
	- Name von Methoden
	- Signaturen der Methoden
	- Attribute
- Interfaces sollen keine eigene Funktionalität beinhalten (Standard-Implementierungen seit Java 8 möglich)
- sie beinhalten ausschließlich abstrakte, öffentliche Methoden
- alle Attribute sind als Konstanten festgelegt
- Deklaration von Interfaces mit dem Schlüsselwort interface
- Interfaces können von anderen Interfaces mit extends abgeleitet (vererbt) werden
- Interfaces können genau wie Klassen als Datentyp für Referenzvariablen genutzt werde

## Implementierung von Interfaces
- Klasse muss Interface implementieren, um dessen Funktionalitäten zu nutzen 
- ```class xyz implements abc{ } ```
- eine Klasse kann mehrere Interfaces importieren
- Objekte einer Klasse sind zu allen Interface-Datentypen kompatibel, sobald die Klasse das Interface implementiert z.B. alle Objekte der Klasse xyz könnten in Referenzvariablen vom Typ abc oder def gespeichert werden
```java
Bookable[] vacationBookings = new Bookable[2];
vacationBookings[0] = new Hotel(75);
vacationBookings[1] = new Airplane(70);
```
## Polymorphie über Interfaces
- analog der [[Kapitel 6 - Vererbung#Polymorphie|Polymorphie über Klassen]], Unterschied:
	- Polymorphie durch Vererbung (Klassen): Objekte einer Subklasse werden in Referenzvariablen vom Typ der Superklasse gespeichert
	- Polymorphie durch Interfaces: Objekte der implementierenden Klasse werden in Referenzvariablen vom Typ des implementierten Interfaces gespeichert
```java
Bookable[] vacationBookings = new Bookable[2];

// Narrowing Cast
vacationBookings[0] = new Hotel(75);  
vacationBookings[1] = new Airplane(70);

for(Bookable bookable : vacationBookings) {  
  // Alle Methodenaufrufe über die Bookable Referenz --> Polymorphie!  
  System.out.println("Freie Plätze: " + bookable.freeSlots());  
  boolean successfullBooking = bookable.bookSlots(73);  
  if(successfullBooking){  
    System.out.println("Buchung erfolgreich - Plätze: " + bookable.freeSlots());  
  }else {  
    System.out.println("Buchung war nicht erfolgreich!");  
  }  
  
  // Widening Cast  
  if(bookable instanceof Hotel currentHotel){  
    currentHotel.clean();  
  }  
}
```