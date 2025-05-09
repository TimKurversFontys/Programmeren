# Opdrachten: UML Klassendiagrammen

## Doel
In deze opdrachten leer je hoe je eenvoudige UML-klassendiagrammen kunt maken. Gebruik de [UML Cheat Sheet](https://scheme360.net/pics/uml-class-diagram-cheat-sheet_1.jpg) als referentie voor de notatie en aanpak. Voor voorbeelden kun je kijken op [GeeksforGeeks](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/). Voor het tekenen van diagrammen kun je tools zoals [draw.io](https://app.diagrams.net/) of [Lucidchart](https://www.lucidchart.com/) gebruiken.

## Opdracht 1: Basis Klassendiagram
Maak een UML-klassendiagram voor een `Student` en een `Course`. Gebruik een associatie om aan te geven dat een student zich kan inschrijven voor meerdere cursussen en dat een cursus meerdere studenten kan hebben.

### Vereisten:
- Voeg attributen toe aan beide klassen (bijvoorbeeld `name` en `studentID` voor `Student`, en `courseName` en `courseCode` voor `Course`).
- Geef de multipliciteit van de associatie weer.

---

## Opdracht 2: Associatie met Rolnamen
Breid het diagram uit met een `Teacher`-klasse. Geef aan dat een `Teacher` meerdere cursussen kan geven, maar dat een cursus slechts één docent heeft. Gebruik rolnamen om de relatie duidelijk te maken. Dit concept heet Multiplicity ofwel multipliciteit.

### Vereisten:
- Voeg attributen toe aan de `Teacher`-klasse (bijvoorbeeld `name` en `employeeID`).
- Gebruik rolnamen zoals `teaches` en `taughtBy` om de associatie te verduidelijken.

---

## Opdracht 3: Complexere Associaties
Voeg een `Department`-klasse toe aan het diagram. Geef aan dat een `Department` meerdere docenten en cursussen kan hebben, maar dat elke docent en cursus slechts tot één afdeling behoort. 

### Vereisten:
- Voeg attributen toe aan de `Department`-klasse (bijvoorbeeld `departmentName` en `departmentCode`).
- Gebruik associaties met correcte multipliciteiten om de relaties weer te geven.

---

## Uitdagende oefening
Bedenk zelf een scenario met minstens drie klassen en teken een UML-klassendiagram. Zorg ervoor dat je gebruik maakt van associaties en multipliciteiten.