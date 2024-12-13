# Lernziele:
- Sie können die Eigenschaften der Programmiersprache Java beschreiben
- Sie kennen die Aufgaben von Compiler, Linker und Interpreter
- Sie können das Zusammenspiel von Bytecode und der Java Virtual Machine erläutern
- Sie können die wesentlichen Java-Tools benennen und ihre Aufgabe beschreiben
- Sie können das Paketkonzept in Java erläutern
- Sie kennen die wesentlichen Systemvariablen im Umfeld von Java
- Sie können Eclipse als Java-Entwicklungsumgebung einsetzen

# Zusammenfassung
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
- kompilierter Code muss für jede Plattform (u.a. Windows, Linux, Mac) einzelnd compiled werden (kann nur auf der jeweils kompilierten Plattform ausgeführt werden)
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
```java class 
HelloWorld {

  public static void main (String[] args){
    System.out.println("Hello to the Java World");

  }
}
```
Quellcode zu Bytecode kompilieren: `javac Helloworld.java`
Ausführen des komplilierten Bytecode in Java Virtial Machine (JVM) `java Helloworld`

## Wesentliche Java Tools
- Java Compiler (javac.exe)
- Java Virtual Machine (JVM) (java.exe)
- javadoc (automatische Erstellung von Dokumentationen)
- Class Loader (lädt Java Klassen in RAM; bereitet Ausführung von Java Applikationen vor)
- Bytecode Verifier (u.a. Überprüfung syntaktische Korrektheit, Klassenhierarchie)

## Wichtige Systemvariablen
- PATH
	- Verzeichnis, in dem sich Java-Tools befinden
- CLASSPATH
	- Verzeichnisse, in denen nach Klassen und Paketen gesucht werden soll
- JAVA_HOME
	- Verzeichnis, in dem das J2SDK installiert wurde
