# Opdracht: Sorteeralgoritme in C#

## Doel
Leer hoe je een eenvoudig sorteeralgoritme schrijft in C# en onderzoek de efficiëntie van je oplossing.

## Instructies

1. **Maak een nieuw C#-bestand:**
    - Open Visual Studio Code.
    - Maak een nieuw bestand aan en sla het op als `Sorteren.cs`.

## Let op
Probeer deze opdracht volledig zelfstandig op te lossen, zonder gebruik te maken van internetbronnen of AI-hulpmiddelen. Zo leer je het meeste!


2. **Schrijf een sorteeralgoritme:**
    - Schrijf zelf (zonder gebruik te maken van internetbronnen of AI) een algoritme dat een array van gehele getallen sorteert van klein naar groot.
    - Voorbeeld van een array om te sorteren:
      ```csharp
      int[] getallen = { 5, 2, 9, 1, 5, 6 };
      ```
    - Laat het gesorteerde resultaat zien met `Console.WriteLine`.

3. **Voer het programma uit:**
    - Open de terminal in Visual Studio Code.
    - Typ `dotnet run` en druk op Enter.
    - Controleer of de array correct gesorteerd wordt weergegeven.

## Uitleg
- **Sorteeralgoritme:** Een reeks instructies waarmee je een lijst van waarden in een bepaalde volgorde zet (bijvoorbeeld van klein naar groot).
- **Array:** Een verzameling van elementen (in dit geval gehele getallen) die je kunt sorteren.

## Extra Oefening

1. **Test met andere arrays:**
    - Probeer je sorteeralgoritme uit met verschillende arrays, bijvoorbeeld lege arrays, arrays met één element, of arrays met dubbele waarden.

2. **Efficiëntie bepalen:**
    - Zoek de Big O Cheat Sheet op (bijvoorbeeld via [bigocheatsheet.com](https://www.bigocheatsheet.com/)).
    - Probeer te bepalen wat de tijdscomplexiteit (Big O) is van jouw sorteeralgoritme.
    - Schrijf in een commentaar in je code welke complexiteit je denkt dat jouw algoritme heeft en waarom.

3. **Implementeer andere sorteeralgoritmes:**
    - Maak gebruik van interfaces om eenvoudig meerdere sorteeralgoritmes toe te kunnen passen, zoals Bubble sort, Insertion sort, Selection sort, Merge sort en Quick sort. Uiteraard mag je nu weer gebruik maken van andere bronnen.
    - Experimenteer met het implementeren van deze verschillende algoritmes en vergelijk hun prestaties en complexiteit.
    - Voeg eventueel een manier toe om het gewenste sorteeralgoritme te kiezen bij het uitvoeren van je programma.

## Extra Uitdaging

4. **Vergelijk theorie en praktijk:**
    - Voeg een timer toe aan je programma (bijvoorbeeld met `System.Diagnostics.Stopwatch`) om de tijd te meten die elk sorteeralgoritme nodig heeft om een array te sorteren.
    - Vergelijk de gemeten tijd met de verwachte efficiëntie volgens de Big O-notatie.
    - Experimenteer met verschillende groottes van arrays en noteer je bevindingen in een tabel of grafiek.
