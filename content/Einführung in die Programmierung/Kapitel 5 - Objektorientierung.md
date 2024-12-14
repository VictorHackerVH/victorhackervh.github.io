Alle Zusammenfassungen: [[Überblick Zusammenfassungen]]

Letztes Kapitel: [[Kapitel 4 - Ausdrücke und Anweisungen]]
Nächstes Kapitel: [[Kapitel 6 - Vererbung]]
# Lernziele
- Sie kennen die Begriffe Klasse, Objekt, Attribut und Methode..
- Sie kennen die Eigenschaften von Attributen und Methoden.
- Sie können Klassen, Attribute und Methoden in der Unified Modelling Language (UML) darstellen.
- Sie können Objekte mithilfe von Konstruktoren erzeugen.
- Sie können das Prinzip der Kapselung im Zusammenhang mit Getter- und Setter-Methoden erläutern.
- Sie kennen die unterschiedlichen Sichtbarkeiten von Attributen und Methoden.
- Sie können Methoden überladen.
- Sie kennen die Begriffe der Klassenattribute und –methoden.
- Sie können Objekte mit dem Garbage Collector zerstören.
- Sie kennen die Begriffe Assoziation, Aggregation und Komposition
# Zusammenfassung
## Einführung in die Objektorientierung
**Klassen**
- Klassen bilden den Bauplan (die Schablone) für Objekte
- nach dem Bauplan können mehrere Objekte erzeugt werden
**Objekte**
- stellen die sog. Instanz einer Klasse dar - werden aus dem Bauplan erstellt, und haben die Eigenschaften nach der Klasse
- können erzeugt, verändert und zerstört werden
- haben eine Identität und einen Zustand
**Attribute**
- beschreiben die Eigenschaften von Objekten
- beschreiben den Zustand eines Objektes
- sind Variablen oder Konstanten innerhalb eines Objektes
- z.B. Was ein Objekt hat oder ist (blau, PS Anzahl)
**Methoden**
- beschreiben das Verhalten von Objekten
- stellen die Funktionalität von Objekten dar
## Darstellung von Klassen in der UML
Unified Modelling Language
- Klassen werden durch Klassendiagramme dargestellt
	- in den Klassendiagrammen werden festgelegt:
		- der Name der Klasse
		- die Namen und Datentypen der Attribute
		- die Namen und Rückgabewerte der Methoden
		- die Sichtbarkeit von Attributen und Methoden 
			- Sichtbarkeit (-private, [leer] default, +public)
![[Programmieren_DarstellungDerKlassenInUML.png]]
Zusätzliche Infos:
- Klassenattribute werden durch Unterstreichung kenntlich gemacht
- [[Kapitel 5 - Objektorientierung#Beziehungen zwischen Objekten|Assoziationen]] erfolgen durch eine einfache Verbindungslinie zwischen den Klassen
	- ![[Programmieren_Assoziation_UML.png|300]]
- Aggregationen erfolgen durch eine Linie mit einer Raute am Ende, wobei die Raute bei der Aggregatsklasse (dem Ganzen) angesiedelt
	- ![[Programmieren_Aggregation_UML.png.png|300]]
- Kompositionen erfolgen analog der Aggregation mit einer ausgefüllten Raute
	- ![[Programmieren_Komposition_UML.png.png|300]]
- Kardinalität
	- ![[Programmieren_Kardinalität_UML.png.png|300]]
- Darstellung der [[Kapitel 6 - Vererbung|Vererbung]]: nicht ausgefüllter Pfeil, wobei der Pfeil bei der Superklasse ist
	- ![[Programmieren_Vererbung_UML.png.png|400]]
- Abstrakte Klassen und Methoden werden in UML durch kursive Schreibweise kenntlich gemacht
- [[Kapitel 7 - Interfaces|Interfaces]] Darstellung: gestrichelte Striche, nicht ausgefüllte Pfeile
	- ![[Programmieren_Interface_UML.png.png|400]]
## Objekte erzeugen
- Objekte sind Instanzen einer Klasse
- zum Erzeugen von Objekten muss zunächst eine Klasse definiert werden
	- Definition einer Klasse mittels ``class``
	- innerhalb der Klasse werden die entsprechenden Attribute und Methoden zu der Klasse deklariert und implementiert
- Objekte werden wie folgt erzeugt
	- zunächst wird eine Variable vom Typ der Klasse deklariert
	- mit Hilfe des new-Operators wird ein neues Objekt der Klasse instanziiert und muss der Variable zugewiesen werden
	- mit dem new-Operator wird eine spezielle Methode der Klasse implizit aufgerufen, der Konstruktor
## Konstruktoren
- sind spezielle Methoden zum Erzeugen von neuen Objekten einer Klasse
- Konstruktoren tragen den gleichen Namen wie die Klasse
- werden ausschließlich über den new-Operator aufgerufen
- liefern als Ergebnis die Referenz auf das neu geschaffene Objekt zurück
- es existiert ein Standardkonstruktor
	- dieser wird automatisch vom Compiler zur Verfügung gestellt, wenn in der Klassendefinition kein Konstruktor implementiert wurde
	- besitzt keine Übergabeparameter
	- sobald ein Konstruktor in der Klasse implementiert wurde, erzeugt der Compiler keinen Standardkonstruktor mehr
- Konstruktoren können dazu verwendet werden, um die Attribute zu initialisieren
- Bei Neuerstellung von Klasse, bei der man keinen Konstruktor anlegt, gibt es einen Standard-Konstruktor, der die Parameter initialisiert und auf 0 / NULL setzt. 
## Beispiel für Implementierung einer Klasse
```Java
class Auto {

//	Deklaration der Attribute
    int ps;
    float kmh;
    String kfzKZ;
    String marke;

//	Implementierung des Konstruktors
    Auto(){
        ps = 75;
        kmh = 0;
        kfzKZ = "XX-XX 0000";
        marke = "Eigenbau";
    }

//	Implementierung der Methoden
    void beschleunigen(float pluskmh){
        kmh += pluskmh;
    }
    void bremsen(float minuskmh){
        if (kmh - minuskmh >= 0){
            kmh -= minuskmh;
        }
    }
}
```
## Prinzip der Kapselung
- Programmiergrundsatz in objektorientierter Programmierung
- Idee: auf die Attribute eines Objektes wird nicht direkt, sondern über spezielle Methoden zugegriffen
- dazu müssen die Attribute vor der Außenwelt verborgen und vor unerlaubtem Zugriff geschützt werden 
- Ziel: die Werte der Attribute dürfen nur im Sinne des Entwicklers sinnvoll verändert werden -> Plausibilitätsprüfung
- die speziellen Änderungsmethoden:
	- Getter-Methoden dienen zum Auslesen der Attribute
	- Setter-Methoden werden zum Verändern der Attribute verwendet
## Sichtbarkeit von Attributen und Methoden
- ``private``
	- nur innerhalb der Klasse sichtbar
- ``protected``
	- nur innerhalb eines Pakets und in Subklassen (siehe [[Kapitel 6 - Vererbung]]) sichtbar
- ``default``
	- nur innerhalb eines Pakets sichtbar
- ``public`` 
	- von überall sichtbar
	- normalerweise sind die Getter- und Setter-Methoden öffentlich, um auf private Attribute zuzugreifen
```Java
class Auto {

  // Deklaration der gekapselten Attribute
    private int ps;
    private float kmh;
    private String kfzKZ;
    private String marke;

  // Getter- und Setter-Methoden
    public String getKfzKZ() {
        return kfzKZ;
    }

    public void setKfzKZ(String kfzKZ) {
        this.kfzKZ = kfzKZ;
    }

    public float getKmh() {
        return kmh;
    }

    public void setKmh(float kmh) {
        this.kmh = kmh;
    }
}
```
## Zugriff auf Attribute und Methoden
- auf Methoden und Attribute wird in der Punktnotation zugegriffen
```Java
objektname.methode(Übergabeparameter);
objektname.attribut;
```
- Sichtbarkeit der Methoden oder Attribute muss direkten Zugriff zulassen
- call by value: Alle Parameter in Java
- call by reference
	- werden Referenzdatentypen (Objekte) übergeben, steht in der Methode die Referenz auf das Orginalobjekt zur Verfügung
```Java
class AutoTest {
    public static void main(String[] args) {

        Auto bmw = new Auto();
        Auto audi = new Auto();

        bmw.tueren = 5;
        audi.tueren = 3;

        bmw.setKfzKZ("HD-XX 321");
        audi.setKmh(135.7f);

        System.out.println("Der BMW hat das
            Kennzeichen: " + bmw.getKfzKZ());

        System.out.println("Der Audi fährt: " +
            audi.getKmh());
    }
}
```
## Überladene Methoden
- Methoden mit dem gleichen Namen werden innerhalb einer Klasse mehrmals definiert
- die Methoden unterscheiden sich dabei in der Anzahl und/oder in der Typisierung der Übergabeparameter
- die Modifier können dabei unterschiedliche Sichtbarkeiten zulassen
- Ziel: gleichnamige Operationen können mit unterschiedlichen Datentypen als Parameter versorgt werden
- gleichnamige Operationen können unterschiedliche Funktionalität zur Verfügung stellen
- auch Konstruktoren können überladen werden
```Java
class Auto {

//	Deklaration der gekapselten Attribute
    private int ps;
    private float kmh;
    private String kfzKZ;
    private String marke;

//	überladene Konstruktoren und Methoden
        Auto(){
        ps = 75; kmh = 0;
        kfzKZ = "XX-XX 0000"; marke = "Eigenbau";
    }

    public Auto(int ps, float kmh, String kfzKZ, String marke){
        this.ps = ps; this.kmh = kmh;
        this.kfzKZ = kfzKZ; this.marke = marke;
    }

    void beschleunigen(float pluskmh){
        kmh += pluskmh;
    }
    protected void beschleunigen(){
        kmh+= 10;
    }
}
```
## Variable Argumente (varargs)
- können beliebige Anzahl von Werten übergeben
- werden intern bei Java als Array behandelt, können also auch so verwendet werden (in schleifen oder Längenabfrage .length)
- `datentyp...` in der Methodensignatur
- müssen am Ende der Übergabeparameter stehen
- nur ein variables Argument pro Methode
```Java
public class VarargsExample {
    public void sumOfNumbers(int... numbers) {
        int sum = 0;
        for (int number : numbers) {
            sum += number;
        }
        System.out.println("Summe: " + sum);
    }

    public static void main(String[] args) {
        VarargsExample sumUp = new VarargsExample();

        sumUp.sumOfNumbers(1);          // Gibt: "Summe: 1"
        sumUp.sumOfNumbers(1, 2, 3);    // Gibt: "Summe: 6"
        sumUp.sumOfNumbers();           // Gibt: "Summe: 0"
    }
}
```
## Klassenattribute und Methoden
- Klassenattribute und -Methoden existieren unabhängig von einer Instanz der Klasse
- können verwendet werden, ohne das ein Objekt existiert
- Definition durch `static`
- Zugriff über Punktnotation über den Klassennamen
- Darstellung in UML: Klassenattribute und -Methoden werden in UML durch Unterstreichung kenntlich gemacht
> [!info] Static Methoden können NUR auf static Attribute zugreifen
> Kein Zugriff auf Instanzattribute o.ä.

```Java
class Auto {

//	Deklaration der gekapselten Attribute
    private int ps;
    private float kmh;
    private String kfzKZ;
    private String marke;
    private static int autoZaehler = 0;

//	Getter- und Setter-Methoden
    Auto(){
        autoZaehler++;
        ps = 75;
        kmh = 0;
        kfzKZ = "XX-XX 0000";
        marke = "Eigenbau";
    }

    public static int getAutoZaehler() {
        return autoZaehler;
    }

    public static void setAutoZaehler(int autoZaehler) {
        Auto.autoZaehler = autoZaehler;
    }
}
```
## Enumeration
- definiert eine Menge an gültigen Werten
- Konstanten werden als Objekt der Enumklasse instanziiert. 
```Java
public enum CarBrand {
  MERCEDES("$$$"),
  BMW("$$$"),
  FORD("$"),
  TESLA("$$");

  private String priceClass;

  public CarBrand(String priceClass){
    this.priceClass = priceClass;
  }

  public String getPriceClass(){
    return priceClass;
  }
}
```
## Objekte löschen
- nicht mehr benötigte Objekte können durch den Garbage Collector zerstört werden
- benötigte Objekte sind dadurch gekennzeichnet, dass sie noch referenziert sind 
- der Garbage collector ruft den Destruktor eines Objekts
- (Deprecated) Destruktoren sind parameterlose Methoden mit dem Namen `protected void finalize();`
## Beziehungen zwischen Objekten
### Assoziation
beschreibt die Struktur einer Menge von Beziehungen zwischen Objekten
**Aggregation**
- spezielle Form der Assoziation
- ist eine Teil Beziehung
- Aggregationen beschreiben keine existenzielle Bedürfnisse
- Beispiel: Beziehung zwischen Güterwagon und Fracht; der Wagon existiert auch ohne Fracht
**Komposition**
- spezielle Form der Aggregation
	- handelt sich ebenfalls um eine Teil Beziehung
- die Existenz des Ganzen ist im Unterschied zur Aggregation von der Existenz des einzelnen Teils abhängig
- Bsp: Güterzug kann nur dann existieren, wenn min. eine Zuglokomotive und min. ein Güterwagon existiert
### Kardinalität#
Beschreibt die mengen- / zahlenmässige Ausprägung einer Beziehung

| Kardinalität | Beschreibung                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------- |
| 1            | Ein Objekt muss genau einem anderen Objekt zugeordnet sein                                        |
| 0..1         | Es kann ein oder ein Objekt dem anderen Objekt zugeordnet sein                                    |
| 0..n         | Es können beliebig viele Objekte einem anderen Objekt zugeordnet sein                             |
| 1..n         | Es muss mindestens ein, bis hin zu unendlich vielen Objekten einem anderen Objekt zugeordnet sein |
