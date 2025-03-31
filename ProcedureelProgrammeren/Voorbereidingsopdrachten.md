# Opdracht: Controlestructuren in C#

## Doel
Leer hoe je controlestructuren gebruikt in C# door een eenvoudig programma te schrijven dat verschillende condities controleert.

## Instructies
1. **Maak een nieuw C#-bestand:**
   - Open Visual Studio Code.
   - Maak een nieuw bestand aan en sla het op als `Conditions.cs`.

2. **Schrijf je eerste conditionele statement:**
   - Typ de volgende code in `Conditions.cs`:
     ```csharp
     using System;

     class Program
     {
         static void Main()
         {
             int age = 20;

             if (age >= 18)
             {
                 Console.WriteLine("Je bent een volwassene.");
             }
             else
             {
                 Console.WriteLine("Je bent een minderjarige.");
             }
         }
     }
     ```

3. **Voer het programma uit:**
   - Open de terminal in Visual Studio Code (gebruik `Ctrl + `).
   - Typ `dotnet run` en druk op Enter.
   - Je zou de tekst "Je bent een volwassene." in de terminal moeten zien als `age` 18 of ouder is, anders "Je bent een minderjarige."

## Uitleg
- **`if` statement:** Controleert of een conditie waar is. Als dat zo is, wordt de code binnen het `if`-blok uitgevoerd.
- **`else` statement:** Wordt uitgevoerd als de conditie in het `if`-statement niet waar is.
- **`Main` methode:** Dit is het startpunt van elk C#-programma. Wanneer je het programma uitvoert, begint de uitvoering bij de `Main` methode.
- **`class` Program:** Dit definieert een klasse genaamd `Program`. Voor nu kun je dit zien als een container voor je code. We zullen later dieper ingaan op klassen.

## Extra Oefening
1. **Meerdere Condities:**
   - Voeg de volgende code toe aan `Conditions.cs`:
     ```csharp
     int score = 85;

     if (score >= 90)
     {
         Console.WriteLine("Uitstekend!");
     }
     else if (score >= 75)
     {
         Console.WriteLine("Goed gedaan!");
     }
     else if (score >= 50)
     {
         Console.WriteLine("Voldoende.");
     }
     else
     {
         Console.WriteLine("Onvoldoende.");
     }
     ```
   - Voer het programma opnieuw uit en bekijk het resultaat voor verschillende waarden van `score`.

2. **Geneste Conditionele Statements:**
   - Voeg de volgende code toe aan `Conditions.cs`:
     ```csharp
     int temperature = 30;

     if (temperature > 0)
     {
         if (temperature > 25)
         {
             Console.WriteLine("Het is warm.");
         }
         else
         {
             Console.WriteLine("Het is koel.");
         }
     }
     else
     {
         Console.WriteLine("Het is koud.");
     }
     ```
   - Voer het programma opnieuw uit en bekijk het resultaat voor verschillende waarden van `temperature`.

## Switch Statements
1. **Eenvoudige Switch Statement:**
   - Voeg de volgende code toe aan `Conditions.cs`:
     ```csharp
     int day = 3;

     switch (day)
     {
         case 1:
             Console.WriteLine("Maandag");
             break;
         case 2:
             Console.WriteLine("Dinsdag");
             break;
         case 3:
             Console.WriteLine("Woensdag");
             break;
         case 4:
             Console.WriteLine("Donderdag");
             break;
         case 5:
             Console.WriteLine("Vrijdag");
             break;
         case 6:
             Console.WriteLine("Zaterdag");
             break;
         case 7:
             Console.WriteLine("Zondag");
             break;
         default:
             Console.WriteLine("Ongeldige dag");
             break;
     }
     ```
   - Voer het programma opnieuw uit en bekijk het resultaat voor verschillende waarden van `day`.

2. **Switch Statement met Strings:**
   - Voeg de volgende code toe aan `Conditions.cs`:
     ```csharp
     string fruit = "Appel";

     switch (fruit)
     {
         case "Appel":
             Console.WriteLine("Je hebt een appel gekozen.");
             break;
         case "Banaan":
             Console.WriteLine("Je hebt een banaan gekozen.");
             break;
         case "Kers":
             Console.WriteLine("Je hebt een kers gekozen.");
             break;
         default:
             Console.WriteLine("Onbekend fruit.");
             break;
     }
     ```
   - Voer het programma opnieuw uit en bekijk het resultaat voor verschillende waarden van `fruit`.