- Alle Zusammenfassungen: [[Überblick Zusammenfassungen]]

- Letztes Kapitel: [[Kapitel 1 - Einführung]]
- Nächstes Kapitel: [[Kapitel 3 - Datentypen]]
# Lernziele:
- Sie können die Eigenschaften der Programmiersprache Java beschreiben
- Sie kennen die Aufgaben von Compiler, Linker und Interpreter
- Sie können das Zusammenspiel von Bytecode und der Java Virtual Machine erläutern
- Sie können die wesentlichen Java-Tools benennen und ihre Aufgabe beschreiben
- Sie können das Paketkonzept in Java erläutern
- Sie kennen die wesentlichen Systemvariablen im Umfeld von Java (nicht klausurrelevant)

# Kontrollfragen:
1. Beschreiben Sie die wesentlichen Eigenschaften von Java!
2. Beschreiben Sie die Funktionsweise eines Compilers!
3. Welche Aufgaben übernimmt der Linker?
4. Nennen Sie unterschiedliche Interpreter-Arten!
5. Welche Rolle spielen Compiler und Interpreter im Umfeld der Programmiersprache Java?
6. Beschreiben Sie den Prozess von der Erstellung des Quellcodes bis zur Ausführung des Programms in der Programmiersprache Java!
7. Nennen Sie drei wesentliche Java-Tools und beschreiben Sie kurz deren Aufgaben!
8. Beschreiben Sie das Paketkonzept der Programmiersprache Java!
9. Welche wesentlichen Systemvariablen kennen Sie im Java-Umfeld? *nicht Klausurrelevant*
10. Beschreiben Sie die wesentlichen Unterschiede der verschiedenen Editionen im Rahmen der Java 2™ Platform! *nicht Klausurrelevant*
11. Wozu werden die einzelnen Systemvariablen benötigt? *nicht Klausurrelevant*

# Zusammenfassung
## Klassifizierung von Software
- unterschiedliche Softwarearten:
	- Systemsoftware
		- grundlegende Dienste für andere Programme
		- Steuerung des Computersystems
	- Entwicklungssoftware
		- Erstellung und Modifikation von Programmen
		- Übersetzungsprogramme für Programmiersprachen
	- Anwendungssoftware
		- u.a. Programme zur Verarbeitung der Daten, Spiele
## Eigenschaften von Java
- vollständig objektorientiert
- plattformunabhängig
	- übersetzte Java-Programme (Bytecode) sind auf jeder javafähigen Plattform ausführbar
- sicher, robust & unkompliziert
	- kein direkter Speicherzugriff mit \*Pointerarithmetik
	- keine rechnerabstürze durch Programmierfehler
- multithreaded
	- parallele Ausführung von Programmteilen
## Compiler, Linker, Interpreter
**Compiler:**
Übersetzt ein Computerprogramm aus einer Quellsprache in semantisch äquivalentes Programm einer Zielsprache
- ein kompilierter Code wird dem Anwender gegeben
- fertig kompilierter Code muss für jede Plattform (u.a. Windows, Linux, Mac) einzelnd compiled werden (kann nur auf der jeweils kompilierten Plattform ausgeführt werden) 
	- Bei Java wird nur bis Bytecode kompiliert, dadurch trifft dies bei Java nicht zu

**Linker:**
- stellt einzelne Programmmodule zu ausführbaren Programm zusammen
- Statisches Linken: fügt Code aus Funktionsbibliotheken zum Code des Hauptcodes hinzu
- Dynamisches Linken: Zur Laufzeit wird Code geladen (z.B. über DLLs bei Windows)

**Interpreter:**
liest Quellcode, analysiert ihn und führt ihn dann aus - geschieht während Laufzeit des Programmes
- Quellcode wird an Anwender gegeben, und von dort aus interpretiert
- deutlich langsamer als Compiler

Plattformunabhängig durch Bytecode:
(quasi bestes aus beiden Welten)
Compiler kompiliert auf Bytecode -> dieser Bytecode ist plattformunabhängig, wird beim Anwender dann vollends durch JVM interepretiert.

## Vom Quellcode zur Ausführung
![[Programmieren_Tools.png]]

Beispiel: 
- Anlegen einer Datei "HelloWorld.java"
```java 
class HelloWorld {

  public static void main (String[] args){
    System.out.println("Hello to the Java World");

  }
}
```
Quellcode zu Bytecode kompilieren: `javac Helloworld.java`
Ausführen des komplilierten Bytecode in Java Virtial Machine (JVM) `java Helloworld`

## Wesentliche Java Tools
- Java Compiler (javac.exe)
	- Der Java-Compiler übersetzt Java-Quellcode in plattformunabhängigen Bytecode, der von der JVM ausgeführt werden kann.
- Java Virtual Machine (JVM) (java.exe)
	- Die JVM führt den Bytecode aus, indem sie ihn in maschinenspezifischen Code übersetzt und ermöglicht so die plattformunabhängige Ausführung von Java-Programmen.
- javadoc (automatische Erstellung von Dokumentationen)
- Class Loader (lädt Java Klassen in RAM; bereitet Ausführung von Java Applikationen vor)
- Bytecode Verifier (u.a. Überprüfung syntaktische Korrektheit, Klassenhierarchie)
## Paketkonzept von Java
- Eine Klasse wird durch das Schlüsselwort `package Paketname;` einem Paket zugeordnet (erste Codezeile)
- Fehlt das Schlüsselwort, befindet sich die Klasse im Default Packet - d.h. im  `src` Folder.  
- Pakete verfolgen einen gemeinsamen Zweck
- eine Klasse kann eindeutig über das Paket und ihren Namen identifiziert werden
