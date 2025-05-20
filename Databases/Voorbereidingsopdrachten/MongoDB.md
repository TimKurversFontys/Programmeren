# Kwekerij-applicatie uitbreiden: Wisselen tussen MySQL en MongoDB

## 1. Introductie

Je kwekerij-applicatie werkt nu met MySQL. In deze opdracht leer je hoe je de applicatie zo aanpast dat je eenvoudig kunt wisselen tussen MySQL en MongoDB als databron, door gebruik te maken van een interface. Ook krijg je uitleg over de voor- en nadelen van NoSQL (zoals MongoDB) en hoe je de code kunt ombouwen.

---

## 2. Waarom een interface?

Een interface zorgt ervoor dat je applicatie niet direct afhankelijk is van één type database. Je definieert een set methodes (zoals `GetBestellingen()`, `AddKlant()`, etc.) en maakt voor elke databron (MySQL, MongoDB) een aparte implementatie. Zo kun je makkelijk wisselen van databron zonder je hele applicatie te herschrijven.

**Voordelen:**
- Makkelijk wisselen van database (bijvoorbeeld voor testen of migratie).
- Minder dubbele code.
- Beter onderhoudbaar.

---

## 3. Voor- en nadelen van NoSQL (zoals MongoDB)

**Voordelen:**
- Flexibel datamodel: geen vaste tabellen, makkelijk uitbreiden.
- Schaalbaar: goed voor grote hoeveelheden data en hoge snelheid.
- JSON-achtige opslag: handig voor complexe/nestbare data.

**Nadelen:**
- Geen (of beperkte) transacties en relaties zoals in SQL.
- Minder geschikt voor complexe JOINs.
- Minder standaardisatie; structuur kan per document verschillen.

---

## 4. Interface ontwerpen

```csharp
public interface IKwekerijRepository
{
    IEnumerable<Bestelling> GetBestellingen();
    void AddKlant(Klant klant);
    // Voeg hier meer methodes toe zoals nodig
}
```

---

## 5. Implementatie voor MySQL

```csharp
public class MySqlKwekerijRepository : IKwekerijRepository
{
    // Implementeer methodes met MySQL-code zoals in de vorige opdracht
}
```

---

## 6. Implementatie voor MongoDB

```csharp
public class MongoKwekerijRepository : IKwekerijRepository
{
    // Implementeer methodes met MongoDB-code
    ```csharp
    private readonly IMongoCollection<Klant> _klanten;
    private readonly IMongoCollection<Bestelling> _bestellingen;

    public MongoKwekerijRepository()
    {
        var client = new MongoClient("mongodb://localhost:27017");
        var database = client.GetDatabase("kwekerij");
        _klanten = database.GetCollection<Klant>("klanten");
        _bestellingen = database.GetCollection<Bestelling>("bestellingen");
    }

    public IEnumerable<Bestelling> GetBestellingen()
    {
        return _bestellingen.Find(_ => true).ToList();
    }

    public void AddKlant(Klant klant)
    {
        _klanten.InsertOne(klant);
    }
    ```
}
```

**Voorbeeld MongoDB-verbinding:**
```csharp
using MongoDB.Driver;

var client = new MongoClient("mongodb://localhost:27017");
var database = client.GetDatabase("kwekerij");
var klanten = database.GetCollection<Klant>("klanten");
```

---

## 7. Starter code (indien je nog geen code hebt)

### Models

```csharp
public class Klant { public int KlantNr; public string Naam; }
public class Plant { public int PlantNr; public string Soortnaam; }
public class Bestelling { public int BestellingNr; public int KlantNr; public DateTime Datum; }
```

### Programma

```csharp
class Program
{
    static void Main()
    {
        IKwekerijRepository repo = new MySqlKwekerijRepository(); // Of: new MongoKwekerijRepository();
        foreach (var b in repo.GetBestellingen())
        {
            Console.WriteLine($"{b.BestellingNr} - {b.KlantNr} - {b.Datum}");
        }
    }
}
```
### Eenvoudig WinForms-formulier voorbeeld

```csharp
using System;
using System.Windows.Forms;

public class MainForm : Form
{
    private Button btnToonBestellingen;
    private ListBox lstBestellingen;
    private IKwekerijRepository repo;

    public MainForm()
    {
        repo = new MySqlKwekerijRepository(); // Of: new MongoKwekerijRepository();

        btnToonBestellingen = new Button { Text = "Toon Bestellingen", Dock = DockStyle.Top };
        lstBestellingen = new ListBox { Dock = DockStyle.Fill };

        btnToonBestellingen.Click += (s, e) =>
        {
            lstBestellingen.Items.Clear();
            foreach (var b in repo.GetBestellingen())
            {
                lstBestellingen.Items.Add($"{b.BestellingNr} - {b.KlantNr} - {b.Datum.ToShortDateString()}");
            }
        };

        Controls.Add(lstBestellingen);
        Controls.Add(btnToonBestellingen);
        Text = "Kwekerij Bestellingen";
        Width = 400;
        Height = 300;
    }
}

// In je Program.cs:
static class Program
{
    [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.SetCompatibleTextRenderingDefault(false);
        Application.Run(new MainForm());
    }
}
```
---

## 8. Omschrijven naar MySQL

Wil je terug naar MySQL? Implementeer de interface in een klasse die MySQL gebruikt (zoals in de vorige opdracht). Je hoeft alleen de repository te wisselen:

```csharp
IKwekerijRepository repo = new MySqlKwekerijRepository();
```

---

## 9. Omschrijven naar MongoDB

Wil je MongoDB gebruiken? Implementeer de interface in een klasse die MongoDB gebruikt. Je hoeft alleen de repository te wisselen:

```csharp
IKwekerijRepository repo = new MongoKwekerijRepository();
```

---

