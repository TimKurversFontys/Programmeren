# Opdracht: Functies in C#

## Doel
Leer hoe je functies gebruikt in C# door een programma te schrijven dat verschillende wiskundige bewerkingen uitvoert.

## Instructies
1. **Maak een nieuw C#-bestand:**
   - Open Visual Studio Code.
   - Maak een nieuw bestand aan en sla het op als `Functions.cs`.

2. **Schrijf een functie die de som van twee getallen berekent:**
   - Typ de volgende code in `Functions.cs`:
     ```csharp
     using System;

     class Program
     {
         static void Main()
         {
             int result = Add(5, 3);
             Console.WriteLine("De som is: " + result);
         }

         static int Add(int a, int b)
         {
             return a + b;
         }
     }
     ```

3. **Voer het programma uit:**
   - Open de terminal in Visual Studio Code (gebruik `Ctrl + `).
   - Typ `dotnet run` en druk op Enter.
   - Je zou de tekst "De som is: 8" in de terminal moeten zien.

## Uitleg
- **Functie:** Een blok code dat een specifieke taak uitvoert en kan worden hergebruikt.
- **Parameter:** Een waarde die aan een functie wordt doorgegeven.
- **Return type:** Het type waarde dat een functie teruggeeft.

## Extra Oefening
1. **Schrijf een functie die het verschil van twee getallen berekent.**
   - Voeg de volgende code toe aan `Functions.cs`:
     ```csharp
     static int Subtract(int a, int b)
     {
         return a - b;
     }
     ```
   - Roep de functie aan in `Main` en geef het resultaat weer.

2. **Schrijf een functie die het product van twee getallen berekent.**
   - Voeg de volgende code toe aan `Functions.cs`:
     ```csharp
     static int Multiply(int a, int b)
     {
         return a * b;
     }
     ```
   - Roep de functie aan in `Main` en geef het resultaat weer.

3. **Schrijf een functie die de deling van twee getallen berekent en controleer op deling door nul.**
   - Voeg de volgende code toe aan `Functions.cs`:
     ```csharp
     static double Divide(int a, int b)
     {
         if (b == 0)
         {
             Console.WriteLine("Delen door nul is niet toegestaan.");
             return 0;
         }
         return (double)a / b;
     }
     ```
   - Roep de functie aan in `Main` en geef het resultaat weer.

## Uitdagende Oefeningen
1. **Schrijf een functie die de factorial van een getal berekent.**
   - **Hint:** Factorial van een getal `n` is het product van alle positieve gehele getallen kleiner dan of gelijk aan `n`.

2. **Schrijf een functie die controleert of een getal een priemgetal is.**
   - **Hint:** Een priemgetal is een getal groter dan 1 dat alleen deelbaar is door 1 en zichzelf.

3. **Schrijf een functie die de grootste gemene deler (GCD) van twee getallen berekent.**
   - **Hint:** Gebruik het Euclidische algoritme om de GCD te berekenen.