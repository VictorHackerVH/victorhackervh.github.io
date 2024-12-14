Alle Zusammenfassungen: [[Überblick Zusammenfassungen]]

Letztes Kapitel: [[Kapitel 2 - Grundlagen von Java]]
Nächstes Kapitel: [[Kapitel 4 - Ausdrücke und Anweisungen]]
# Lernziele
- Sie kennen die unterschiedlichen einfachen Datentypen in Java
- Sie kennen die Wertebereiche der jeweiligen Datentypen
- Sie können Variablen und Konstanten in Java deklarieren
- Sie kennen die unterschiedlichen Literale
- Sie kennen unterschiedliche Standard-Escape-Sequenzen und können diese einsetzen
- Sie kennen die Konvertierungsvorschriften bezüglich der einfachen Datentypen
- Sie können den Aufbau von Arrays beschreiben
- Sie können Arrays in Java deklarieren
- Sie kennen den theoretischen Umgang mit Referenzdatentypen
- Sie kennen die speziellen Referenzdatentypen Array und String
# Zusammenfassung
## Arten von Datentypen
- Primitive Datentypen
	- bool‘sche Typen sind Wahrheitswerte: True und False
	- numerische Typen
		- Byte, Short, Integer und Long: Menge der ganzen Zahlen
		- Double und Float: Menge der reellen Zahlen
	- alphanumerisch
		- Char: Menge der vereinbarten Schriftzeichen, z.B. ASCII-Zeichensatz
- [[Kapitel 3 - Datentypen#Referenzdatentypen|komplexe Datentypen]]
	- Referenzdatentypen: Individuell definierte Datentypen
		- String: Verkettung von Character-Werten ⇒ Zeichenketten
		- Array: Definition eines n-dimensionalen Feldes

| Typname |     |
| ------- | --- |
| boolean |     |
## Deklaration von Variablen in Java
**Deklaration von Variablen:**
`Typname Variablenname;`
Deklaration mit Initialisierung:
`Typname Variablenname = Wert;`
**Deklaration von Konstanten:**
- Werden ähnlich wie Variablen deklariert, vor Typname kommt Schlüsselwort *final*
- Können nur einmalig initialisiert werden
`final double pi = 3,142;`
## Literale 
Ein Literal in der Programmiersprache bezeichnet fest definierte Zeichenfolge zur Darstellung von Werten für Basis-Datentypen.
**Numerische Literale:**
**Ganzzahlen:**
- Dezimalliterale (Ziffern 0 bis 9)
- Oktalliterale (Präfix 0, und dann Ziffern 0 bis 7)
- Hexadezimalliterale (Präfix 0x, dann 0 bis 9 und A bis F
**Fließkommazahlen:**
- Besteht aus Vor- und Nachkommateil, getrennt durch einen Dezimalpunkt
- Suffixe f und d durch float und double
- Exponent wird durch ein E bzw. e eingeleitet
- Vor- oder Nachkommateil darf ausgelassen werden
**Alphanumerische Literale:**
- boolean
- char
- String

## Standard Escape Sequenzen
Zeichenliterale können Standard-Escape-Sequenzen zur Darstellung von Sonderzeichen beinhalten

| Zeichen | Bedeutung                   |
| ------- | --------------------------- |
| \t      | Tabulator                   |
| \n      | Zeilenschaltung             |
| \\"     | Doppeltes Anführungszeichen |
| \uxxxx  | Unicodezeichen              |
## Konvertierungsregeln
Generelle Unterscheidung in erweiternde und einschränkende Konvertierung
![[Programmieren_Konvertierungsregeln.png]]

## Arrays in Java
- semidynamisch: ihre Größe kann zur Laufzeit festgelegt, aber danach nicht mehr verändert werden
- sind Objekte und bieten verschiedene Methoden
- Deklaration gleich wie bei Variablen, nur eckige Klammern bei Typname oder an Variablennamen
- Initialisierung durch new Operator oder durch Zuweisung eines Array-Literals
```java
int[] zahl = {1, 2, 3, 4, 5};
int[][] matrix = new int[3][3];
```

## Referenzdatentypen
- im Gegensatz zu einfachen Datentypen handelt es sich hierbei um komplex Typen
- zu den Referenztypen zählen
	- Objekte ([[Kapitel 5 - Objektorientierung]])
	- Strings
	- Arrays
- Strings und Arrays sind besondere Objekte
- bei einfachen Datentypen reicht die Deklaration der Variablen aus, während Referenztypen mittels des new-Operators noch erzeugt werden müssen (Ausnahmen Strings und Arrays)
- Referenztypen stellen lediglich einen Verweis auf Objekte dar