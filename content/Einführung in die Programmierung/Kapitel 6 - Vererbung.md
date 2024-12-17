Alle Zusammenfassungen: [[Überblick Zusammenfassungen]]

Letztes Kapitel: [[Kapitel 5 - Objektorientierung]]
Nächstes Kapitel: [[Kapitel 7 - Interfaces]]
# Lernziele
- Sie können die Eigenschaften der Vererbung beschreiben.
- Sie können den Unterschied von Super- und Subklassen beschreiben und den Begriff der Vererbungshierarchie erläutern.
- Sie können die Begriffe Generalisierung und Spezialisierung im Zusammenhang mit der Vererbung erklären.
- Sie können Vererbungsbeziehungen in der UML darstellen.
- Sie können das Vererbungskonzept in Java beschreiben.
- Sie kennen die Eigenschaften der Klasse Object.
- Sie können Methoden überschreiben.
- Sie kennen die Bedeutung der Modifier abstract und final.
- Sie können die Bedeutung von this und super erklären.
- Sie kennen die Konzepte des narrowing und widening casts.
- Sie können den Begriff der Polymorphie erklären.

# Zusammenfassung
## Eigenschaften der Vererbung
- eine Unterklasse (Subklasse) erbt die Attribute und Methoden einer Oberklasse (Superklasse)
- es entsteht eine Vererbungshierarchie, die theoretisch beliebig tief geschachtelt werden kann
- i.d.R. besitzt die Subklasse noch zusätzliche Attribute und Methoden
- Ziel und Vorteil: bestehender Programmcode kann wieder verwendet werden (Reuse)

Vererbung erfolgt durch folgende Syntax:
```JAVA
class Subklasse extends Superklasse { }
```
mit extends verweist die Subklasse auf ihre Superklasse

- alle Attribute und Methoden mit Ausnahme der Konstruktoren der Superklasse werden an die Subklasse vererbt
- in der Subklasse kann die Funktionalität der abgeleiteten Klasse erweitert und verändert werden
	- Hinzufügen von Methoden und Attributen
	- Überladen von Methoden
	- Überschreiben von Methoden
## Die Superklasse Object
von ihr sind alle Klassen explizit oder implizit abgeleitet, jede eigene Klasse ist also immer eine Subklasse von Object.
Damit stehen alle Methoden der Klasse Object in allen abgeleiteten Klassen zur Verfügung:
- Object() – parameterloser Konstruktor
- toString() – Konvertierung eines Objekts in einen String ausgeführt
- equals() – vergleicht zwei Objekte miteinander
- hashCode() – berechnet den Hashwert eines Objektes
- clone() – kopiert zwei Objekte
- finalize() – ist der Destruktor
## Sichtbarkeit von Methoden und Attributen
- `private`
	- nur innerhalb der Klasse sichtbar
- `protected`
	- nur innerhalb eines Paketes und in Subklassen sichtbar
- `default`
	- nur innerhalb des Paketes
- `public`
	- von überall sichtbar
	- normalerweise sind die Getter- und Setter-Methoden öffentlich, um auf private Attribute zuzugreifen
## Methoden überschreiben
Methoden überschreiben ≠ [[Kapitel 5 - Objektorientierung#Überladene Methoden|Methoden überladen]]
- Methoden, die in der Superklasse definiert sind, können in Subklassen erneut definiert werden
- zur Laufzeit wird entschieden, welche Methode konkret ausgeführt wird:
	1. JVM sucht zunächst in Klasse des Referenzdatentypen nach einer passenden Methode
	2. wird dort keine passende Methode gefunden, wird die Vererbungshierarchie von unten nach oben nach einer passenden Methode durchsucht
- erfordert zusätzliche Rechnerkapazität
- `final`: verhindert explizit das überschreiben
- überschreibende Methode muss mindestens so sichtbar wie die überschriebene Methode sein
```java
public enum CarBrand {
  MERCEDES("$$$"),
  BMW("$$$"),
  FORD("$"),
  TESLA("$$"){
        @Override
        public String toString() { //Überschrieb der toString Methode von Carbrand
            return super.toString() + " voll elektrisch";
        }
    };

  // ...

  @Override
    public String toString() {
        return switch(this){
            case TESLA -> "Tesla";
            case FIAT -> "Fiat";
            case MERCEDES -> "Mercedes";
            case BMW -> "BMW";
        } +  "(" + priceClass + ")";
    }
}
```

## Weitere Modifier
- `abstract` 
	- noch nicht ausreichend spezialisiert und dienen nur als grobe Vorlage für Subklassen
	- von abstrakten Klassen können keine Objekte erzeugt werden
	- beinhaltet eine Klasse min. eine abstrakte Methode, so muss die Klasse abstrakt werden
	- Subklassen von abstrakten superklassen müssen alle abstrakten Methoden der Superklasse implementieren oder selbst abstrakt werden
- `final`
	- Klassen mit dem Modifier final dürfen keine Subklassen mehr bilden
	- Methoden mit dem Modifier final dürfen nicht überschrieben werden. 
	- Final Attribute sind Konstanten, die nicht überschrieben werden können.  
## Bedeutung von this und super
- mit `.super` kann auf Methoden und Attribute der Superklasse zugegriffen werden
	- ein kaskadierender Aufruf super.super ist nicht möglich
- `this` ist eine referenzvariable, die beim Anlegen des Objekts automatisch erzeugt wird, und auf das aktuelle Objekt zeigt. 
	- es können eigene Methoden, Instanz und Klassenattribute angesprochen werden
- mithilfe von `this(Übergabeparamter);` oder `super(Übergabeparameter);` können Konstruktoren verkettet werden
## Narrowing Cast
- Objekte von Subklassen können in Referenzvariablen gespeichert werden, die vom Typ ihrer Superklasse sind
- dabei wird nur die Sicht auf die Objekte beschränkt, d.h. es sind nur noch die Attribute und Methoden sichtbar, die in der Superklasse deklariert sind
- die subklassen-spezifischen Attribute und Methoden sind noch vorhanden, aber vorübergehend ausgeblendet
- wesentliche Voraussetzung für die Polymorphie
## Widening Cast
- es handelt sich dabei um eine unsichere Konvertierung
- es muss sichergestellt werden, dass es sich bei den Referenzen um Referenzen auf Objekte der Subklasse handelt
- vor der Umwandlung muss der Typ der Referenz mit dem Operator instanceof überprüft werden ⇒ `referenzvariable instanceof Subklasse` muss true ergeben
- bei der Durchführung muss ein expliziter Cast auf den Typ der Subklasse durchgeführt werden

- der widening cast wechselt von einer Sicht mit weniger auf eine Sicht mit mehr Details und blendet die subklassen-spezifischen Attribute und Methoden wieder ein
## Polymorphie
Die Polymorphie basiert genau auf diese Möglichkeiten des Narrowing und Widening Cast

```java
Dog myDog = new Dog(50.0f, 65f, "Bello", "Schäferhund");


Animal myAnimal = myDog; // Narrowing Cast --> Sichtbarkeit wird eingeschränkt

myAnimal.move(); 
myAnimal.eat();  
myAnimal.breath();
// myAnimal.bark(); // nicht möglich -> nicht mehr Sichtbar 

Animal[] animalShelter = new Animal[3];
// Narrowing Cast  
animalShelter[0] = myDog;  
animalShelter[1] = myBird;   
animalShelter[2] = new Bird(10, 30, "Lorenzo", false);

for(Animal currentAnimal : animalShelter) {  
  currentAnimal.eat();  
  currentAnimal.breath();  
  currentAnimal.move();  
  
  if(currentAnimal instanceof Dog) {  
    // ((Dog)currentAnimal).bark(); Kurzform  
    Dog currentDog = (Dog)currentAnimal;  
    currentDog.bark();  
  }
}
```
