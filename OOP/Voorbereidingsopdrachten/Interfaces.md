## Wat is een Interface?

Een **interface** is een contract dat aangeeft welke methoden een klasse moet implementeren. Het definieert alleen de handtekeningen van methoden, zonder enige implementatiedetails. Dit maakt interfaces een krachtig hulpmiddel om flexibiliteit en uitbreidbaarheid in je code te waarborgen.

### Kenmerken van een Interface
- Een interface bevat alleen methoden, eigenschappen, indexers of events zonder implementatie.
- Klassen of structuren die een interface implementeren, moeten alle leden van de interface definiëren.
- Interfaces ondersteunen meervoudige implementatie, wat betekent dat een klasse meerdere interfaces kan implementeren.

### Waarom Interfaces Gebruiken?
1. **Losse koppeling**: Door interfaces te gebruiken, kun je de afhankelijkheid tussen klassen verminderen. Dit maakt je code eenvoudiger te onderhouden en te testen.
2. **Flexibiliteit**: Je kunt eenvoudig verschillende implementaties van een interface uitwisselen zonder de rest van je code te wijzigen.
3. **Testbaarheid**: Interfaces maken het mogelijk om mock-implementaties te gebruiken tijdens het testen, zoals in deze opdracht met mock data.

### Voorbeeld
Stel je voor dat je een applicatie bouwt die gegevens uit verschillende bronnen moet ophalen, zoals bestanden, een database of een API. Door een interface te definiëren, kun je een uniforme manier creëren om met deze gegevensbronnen te werken, ongeacht hun specifieke implementatie.

```csharp
public interface IDataProvider
{
    List<string> GetData();
}
```

### Complexere Vervolgopdracht: Uitbreiding met Meerdere Interfaces

Nu je bekend bent met het implementeren van een enkele interface, gaan we een stap verder door meerdere interfaces te combineren. Dit helpt je om de kracht van interfaces in complexere scenario's te begrijpen.

#### Opdracht: Meerdere Interfaces Implementeren
Je gaat een applicatie bouwen waarin gegevens niet alleen worden opgehaald, maar ook worden verwerkt en opgeslagen. Hiervoor definieer je drie interfaces:

1. `IDataProvider` (zoals eerder gedefinieerd) voor het ophalen van gegevens.
2. `IDataProcessor` voor het verwerken van gegevens.
3. `IDataSaver` voor het opslaan van gegevens.

##### 1. Definieer de Nieuwe Interfaces
Voeg de volgende interfaces toe aan je project:

```csharp
public interface IDataProcessor
{
    List<string> ProcessData(List<string> data);
}

public interface IDataSaver
{
    void SaveData(List<string> data);
}
```

##### 2. Implementeer de Interfaces
Maak klassen die deze interfaces implementeren:

**DataProcessor**: Verwerkt gegevens door bijvoorbeeld alle tekst naar hoofdletters te converteren.

```csharp
using System.Collections.Generic;
using System.Linq;

public class DataProcessor : IDataProcessor
{
    public List<string> ProcessData(List<string> data)
    {
        return data.Select(d => d.ToUpper()).ToList();
    }
}
```

**FileDataSaver**: Slaat gegevens op in een bestand.

```csharp
using System.Collections.Generic;
using System.IO;

public class FileDataSaver : IDataSaver
{
    private readonly string _filePath;

    public FileDataSaver(string filePath)
    {
        _filePath = filePath;
    }

    public void SaveData(List<string> data)
    {
        File.WriteAllLines(_filePath, data);
    }
}
```

##### 3. Combineer Alles in je Programma
Pas je programma aan om gegevens op te halen, te verwerken en op te slaan.

```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        // Kies een gegevensbron
        IDataProvider dataProvider;
        IDataProcessor dataProcessor = new DataProcessor();
        IDataSaver dataSaver;

        Console.WriteLine("Kies een gegevensbron: (1) Bestand, (2) Mock");
        string keuze = Console.ReadLine();

        if (keuze == "1")
        {
            dataProvider = new FileDataProvider("data.txt");
            dataSaver = new FileDataSaver("output.txt");
        }
        else
        {
            dataProvider = new MockDataProvider();
            dataSaver = new FileDataSaver("mock_output.txt");
        }

        // Haal gegevens op
        try
        {
            var data = dataProvider.GetData();
            Console.WriteLine("Opgehaalde gegevens:");
            foreach (var item in data)
            {
                Console.WriteLine(item);
            }

            // Verwerk gegevens
            var processedData = dataProcessor.ProcessData(data);
            Console.WriteLine("\nVerwerkte gegevens:");
            foreach (var item in processedData)
            {
                Console.WriteLine(item);
            }

            // Sla gegevens op
            dataSaver.SaveData(processedData);
            Console.WriteLine("\nGegevens succesvol opgeslagen.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Fout: {ex.Message}");
        }
    }
}
```

##### 4. Reflectie
- Wat zijn de voordelen van het gebruik van meerdere interfaces in dit scenario?
- Hoe kun je deze structuur uitbreiden om nog meer functionaliteit toe te voegen?
- Wat zijn mogelijke nadelen van het gebruik van interfaces in complexe applicaties?

Met deze opdracht leer je hoe je meerdere interfaces kunt combineren om een flexibele en uitbreidbare applicatie te bouwen.
