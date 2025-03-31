# Opdracht: Lussen in C#

## Doel
Leer hoe je lussen gebruikt in C# door eenvoudige programma's te schrijven die verschillende soorten lussen demonstreren en zelf problemen op te lossen.

## Instructies
1. **Maak een nieuw C#-bestand:**
   - Open Visual Studio Code.
   - Maak een nieuw bestand aan en sla het op als `Loops.cs`.

2. **Schrijf je eerste `while`-lus:**
   - Typ de volgende code in `Loops.cs`:
     ```csharp
     using System;

     class Program
     {
         static void Main()
         {
             int count = 0;

             while (count < 5)
             {
                 Console.WriteLine("Count is: " + count);
                 count++;
             }
         }
     }
     ```

3. **Voer het programma uit:**
   - Open de terminal in Visual Studio Code (gebruik `Ctrl + `).
   - Typ `dotnet run` en druk op Enter.
   - Je zou de tekst "Count is: 0" tot en met "Count is: 4" in de terminal moeten zien.

## Uitleg
- **`while`-lus:** Voert de code binnen de lus uit zolang de conditie (`count < 5`) waar is.

## Extra Oefening
1. **`for`-lus:**
   - Voeg de volgende code toe aan `Loops.cs`:
     ```csharp
     for (int i = 0; i < 5; i++)
     {
         Console.WriteLine("i is: " + i);
     }
     ```
   - Voer het programma opnieuw uit en bekijk het resultaat.

2. **`foreach`-lus:**
   - Voeg de volgende code toe aan `Loops.cs`:
     ```csharp
     string[] fruits = { "Appel", "Banaan", "Kers" };

     foreach (string fruit in fruits)
     {
         Console.WriteLine("Fruit: " + fruit);
     }
     ```
   - Voer het programma opnieuw uit en bekijk het resultaat.

## Uitdagende Oefeningen
1. **Som van Even Getallen:**
   - Schrijf een programma dat de som van alle even getallen tussen 1 en 100 berekent en weergeeft. Gebruik hiervoor een `for`-lus.
   - **Hint:** Gebruik de modulus operator (`%`) om te controleren of een getal even is.

2. **Zoek een Woord:**
   - Schrijf een programma dat een array van strings doorzoekt naar een specifiek woord. Gebruik hiervoor een `foreach`-lus.
   - **Hint:** Vraag de gebruiker om een woord in te voeren en controleer of dit woord in de array voorkomt.

3. **Factorial Berekening:**
   - Schrijf een programma dat de factorial van een gegeven getal berekent. Gebruik hiervoor een `while`-lus.
   - **Hint:** Factorial van een getal `n` is het product van alle positieve gehele getallen kleiner dan of gelijk aan `n`.
