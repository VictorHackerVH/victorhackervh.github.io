- Alle Zusammenfassungen: [[Überblick Zusammenfassungen]]

- Letztes Kapitel: [[Kapitel 3 - Datentypen]]
- Nächstes Kapitel: [[Kapitel 5 - Objektorientierung]]
# Lernziele
- Sie kennen die Begriffe Ausdrücke und Anweisungen
- Sie kennen die unterschiedlichen Arten von Operatoren
    - arithmetisch
    - relational
    - logisch
    - Zuweisung
    - sonstige
- Sie kennen die Verzweigungsmöglichkeiten mit der IF- und der SWITCH-Anweisung
- Sie kennen die unterschiedlichen Schleifentypen
    - kopfgesteuert
    - fußgesteuert
    - zählend
- Sie kennen die break- und continue-Anweisung
# Kontrollfragen
1. Was verstehen Sie im Zusammenhang mit Programmierung unter dem Begriff „Ausdruck?
2. Woraus setzen sich Ausdrücke zusammen?
3. Zählen Sie unterschiedliche Operatoren auf! Unterscheiden Sie dabei die Operatoren nach dem Typ der Operanden!
4. Erläutern Sie den Fragezeichenoperator anhand des folgenden Codings!

```Java
String X = (a == b) ? “Ja“ : “Nein“;
```

5. Definieren Sie den Begriff „Anweisung“ im Sinne der Programmierung!
6. Welche Möglichkeiten bietet Ihnen die Programmiersprache Java, um Verzweigungen zu realisieren?
7. Erläutern Sie den Begriff „dangling else“!
8. Welche Bedeutung messen Sie der Break-Anweisung im Zusammenhang mit der Switch-Anweisung bei?
9. Nennen Sie die unterschiedlichen Schleifenarten in Java und beschreiben Sie deren Verhalten!
10. Worin besteht der wesentliche Unterschied zwischen einer kopf- und einer fußgesteuerten Schleife?
11. Beschreiben Sie den Schleifenkopf einer For-Schleife!
12. Was bewirken die Break- und die Continue-Anweisung innerhalb einer Schleife?
# Ausdrücke
(auch bei [[Kapitel 1 - Einführung#Programmierung Grundbegriffe|Grundbegriffe der Informatik]])
Ausdrücke sind die kleinste ausführbare Einheit in einem Programm
Ausdrücke haben folgende Aufgaben: 
- Variablen Werte zuzuweisen
- numerische Berechnungen durchzuführen
- logische Bedingungen zu formulieren
Ausdrücke bestehen aus mindestens einem Operator und einem oder mehreren Operanden, auf die der Operator angewendet wird
Unterscheidung der Operatoren nach dem Typ der Operanden
- arithmetische Operatoren (+, -, \*, %, ++, -- )
- relationale Operatoren
	- ``==`` gleich; ``!=`` ungleich; "``<``,``>``, ``<=``, ``>=``"
- logische Operatoren
	- ``!`` logisches nicht; ``&&`` UND mit Short Circuit Evaluation; ``||`` ODER mit Short Circuit
	- ``&``, ``|`` ohne Short Circuit Evaluation (beide Teilausdrücke werden ausgewertet)
	- `^` ergibt true, wenn beide Ausdrücke einen unterschiedlichen Wahrheitswert haben
- (bitweise Operatoren)
- Zuweisungsoperatoren
	- ``=`` einfache Zuweisung
	- ``/=`` Divisionszuweisung
	- ``%=`` Modulozuweisung
- sonstige Operatoren
	- Der Fragezeichenoperator 
```java
	a ? b : c; // ==> results in b if a is true or c if a is false
```
- String Verkettung: mit dem ``+`` Operator können auch Strings verkettet werden
## Anweisungen
- die leere Anweisung:
```
;
```
Anweisungsblock
- ist eine Zusammenfassung von Anweisungen
- wird als einzelne Anweisung behandelt und wird dort verwendet, wo syntaktisch nur eine Anweisung erlaubt ist
## Verzweigungen

> [!attention] If Anweisung wurde hier übersprungen
> ([Link zum Script](https://matthiasbergneels.github.io/md-scripts/01_Programmieren_Vorlesung/Programmierenskript_1.Semester.html#/35/1))

**Switch Anweisung:**
- bietet die Möglichkeit der Mehrfachverzweigung
- Ablauf:
	- der ausdruck wird zunächst ausgewertet
	- das Ergebnis wird mit den Konstanten der case-Label verglichen und bei Gleichheit die Anweisung und alle nachstehenden Anweisungen ausgeführt (Fall-Through-Logik)
	- dies kann durch Einsatz einer break-Anweisung verhindert werden
	- jede Konstante darf nur einmal auftauchen
	- gibt es keine passende Konstante, wird das optionale default-Label am Ende der switch-Anweisung angesprungen
```JAVA
switch (ausdruck) {
  case constant1:
    anweisung1;
  case constant2:
    anweisung2;
  // …
  default:
    default_anweisung;}
```
**Switch Expression (Seit Java 14):**
keine Fall-Through-Logik
Einzelne Anweisung ODER Anweisungsblock pro Fall
```Java
int numLetters = switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> 6;
    case TUESDAY -> 7;
    default -> {
      String s = day.toString();
      int result = s.length();
      yield result;
    }
};
```

**Schleife:**

> [!attention] Schleifen wurden zu großen Teilen übersprungen
> [Link zum Script](https://matthiasbergneels.github.io/md-scripts/01_Programmieren_Vorlesung/Programmierenskript_1.Semester.html#/36)

- besondere For Schleife zum Durchlaufen von Feldern:
```Java
for ( Typ Bezeicher : Feld )
```

**Break und Continue Anweisung:**
- beide Anweisungen dienen der Änderung des Ablaufs innerhalb von Schleifen
- die break-Anweisung
    - eine break-Anweisung innerhalb einer Schleife führt zum Verlassen der Schleife
- die continue-Anweisung
    - der aktuelle Schleifendurchlauf wird beendet und das Programm springt zum Ende der Schleife
    - ein neuer Durchlauf der Schleife mit Prüfung der Abbruchbedingung beginnt
