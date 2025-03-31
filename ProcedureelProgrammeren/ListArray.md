# Opdracht: Werken met Lijsten en Arrays in C#

## Doel
Leer hoe je lijsten en arrays gebruikt in C# door eenvoudige programma's te schrijven die verschillende operaties op lijsten en arrays demonstreren.

## Instructies
1. **Maak een nieuw C#-bestand:**
   - Open Visual Studio Code.
   - Maak een nieuw bestand aan en sla het op als `ListsAndArrays.cs`.

2. **Schrijf je eerste array-manipulatie:**
   - Typ de volgende code in `ListsAndArrays.cs`:
     ```csharp
     using System;

     class Program
     {
         static void Main()
         {
             int[] numbers = { 1, 2, 3, 4, 5 };

             for (int i = 0; i < numbers.Length; i++)
             {
                 Console.WriteLine("Number: " + numbers[i]);
             }
         }
     }
     ```

3. **Voer het programma uit:**
   - Open de terminal in Visual Studio Code (gebruik `Ctrl + `).
   - Typ `dotnet run` en druk op Enter.
   - Je zou de getallen 1 tot en met 5 in de terminal moeten zien.

## Uitleg
- **Array:** Een verzameling van elementen van hetzelfde type. Arrays hebben een vaste grootte.
- **`for`-lus:** Wordt gebruikt om door de elementen van de array te itereren.

## Extra Oefening
1. **Lijst Manipulatie:**
   - Voeg de volgende code toe aan `ListsAndArrays.cs`:
     ```csharp
     using System;
     using System.Collections.Generic;

     class Program
     {
         static void Main()
         {
             List<string> fruits = new List<string> { "Appel", "Banaan", "Kers" };

             foreach (string fruit in fruits)
             {
                 Console.WriteLine("Fruit: " + fruit);
             }
         }
     }
     ```
   - Voer het programma opnieuw uit en bekijk het resultaat.

## Uitdagende Oefeningen
1. **Array Omkeren:**
   - Schrijf een programma dat een array van getallen omkeert en de omgekeerde array weergeeft.
   - **Hint:** Gebruik een `for`-lus om door de array te itereren en de elementen in omgekeerde volgorde weer te geven.

2. **Elementen Toevoegen aan een Lijst:**
   - Schrijf een programma dat de gebruiker toestaat om elementen aan een lijst toe te voegen totdat de gebruiker "stop" invoert. Geef vervolgens alle elementen in de lijst weer.
   - **Hint:** Gebruik een `while`-lus en de `Add`-methode van de `List`-klasse.

3. **Zoeken in een Array:**
   - Schrijf een programma dat controleert of een bepaald getal in een array voorkomt. Vraag de gebruiker om een getal in te voeren en geef een bericht weer of het getal in de array voorkomt.
   - **Hint:** Gebruik een `foreach`-lus om door de array te itereren en vergelijk elk element met het ingevoerde getal.