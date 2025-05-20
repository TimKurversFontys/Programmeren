# Opdracht: C# Applicatie met MySQL Database (Kwekerij)

## Doel
Je leert een eenvoudige C#-applicatie bouwen die verbinding maakt met een MySQL-database (bijvoorbeeld via XAMPP), gegevens uitleest en JOINS gebruikt. Je mag kiezen voor WinForms, ASP.NET of een Console-applicatie.

---

## Stap 1: Database opzetten

1. **Installeer MySQL** via XAMPP of een andere oplossing.  
    Zie de [officiële MySQL installatiehandleiding](https://dev.mysql.com/doc/refman/8.0/en/installing.html) voor meer informatie.
2. **Maak de database en tabellen aan** 

> **Opmerking:** Gebruik het ERD dat je zelf hebt ontworpen in de opdrachten [ERD.md] en [Databasediagram.md] als basis voor het aanmaken van je database en tabellen. Schrijf zelf het benodigde SQL-script om de structuur van jouw kwekerijdatabase aan te maken, gebaseerd op jouw eigen datamodel.
>
> **Mocht je geen eigen ERD hebben, gebruik dan onderstaand voorbeeldscript:**
>
> ```sql
> CREATE DATABASE IF NOT EXISTS kwekerij;
> USE kwekerij;
>
> CREATE TABLE Klant (
>   KlantNr INT PRIMARY KEY AUTO_INCREMENT,
>   Naam VARCHAR(100) NOT NULL
> );
>
> CREATE TABLE Plant (
>   PlantNr INT PRIMARY KEY AUTO_INCREMENT,
>   Soortnaam VARCHAR(100) NOT NULL
> );
>
> CREATE TABLE Bestelling (
>   BestellingNr INT PRIMARY KEY AUTO_INCREMENT,
>   KlantNr INT,
>   Datum DATE,
>   FOREIGN KEY (KlantNr) REFERENCES Klant(KlantNr)
> );
>
> CREATE TABLE BestellingPlant (
>   BestellingNr INT,
>   PlantNr INT,
>   Aantal INT,
>   PRIMARY KEY (BestellingNr, PlantNr),
>   FOREIGN KEY (BestellingNr) REFERENCES Bestelling(BestellingNr),
>   FOREIGN KEY (PlantNr) REFERENCES Plant(PlantNr)
> );
> ```
>
> 3. **Vul de tabellen met enkele testgegevens**.
```sql
INSERT INTO Klant (Naam) VALUES
    ('Jan Jansen'),
    ('Piet Pieters'),
    ('Anna de Vries');

INSERT INTO Plant (Soortnaam) VALUES
    ('Ficus'),
    ('Monstera'),
    ('Sansevieria');

INSERT INTO Bestelling (KlantNr, Datum) VALUES
    (1, '2024-05-01'),
    (2, '2024-05-03'),
    (3, '2024-05-05');

INSERT INTO BestellingPlant (BestellingNr, PlantNr, Aantal) VALUES
    (1, 1, 2),
    (1, 2, 1),
    (2, 2, 3),
    (2, 3, 2),
    (3, 1, 1),
    (3, 3, 4);
```
---

## Stap 2: C# Project aanmaken

1. Maak een nieuw C#-project aan (WinForms, ASP.NET of Console).
2. Voeg de [MySql.Data NuGet package](https://www.nuget.org/packages/MySql.Data/) toe.

---

## Stap 3: Verbinding maken met de database

```csharp
using MySql.Data.MySqlClient;

string connStr = "server=localhost;user=root;database=kwekerij;port=3306;password=JOUW_WACHTWOORD";
using (var conn = new MySqlConnection(connStr))
{
    try
    {
        conn.Open();
        // Testverbinding
        Console.WriteLine("Verbinding gelukt!");
    }
    catch (Exception ex)
    {
        Console.WriteLine("Fout bij verbinden: " + ex.Message);
    }
}
```
### Uitleg: try-catch-finally en using

- **try-catch-finally**:  
    Met een `try`-blok probeer je code uit te voeren die fouten kan veroorzaken (zoals het openen van een databaseverbinding).  
    Als er een fout optreedt, wordt de `catch` uitgevoerd, waarin je de fout kunt afhandelen (bijvoorbeeld een foutmelding tonen).  
    Het `finally`-blok wordt altijd uitgevoerd, of er nu een fout was of niet, en wordt vaak gebruikt om op te ruimen (zoals verbindingen sluiten).

    Voorbeeld:
    ```csharp
    MySqlConnection conn = null;
    try
    {
            conn = new MySqlConnection(connStr);
            conn.Open();
            // Code die de verbinding gebruikt
    }
    catch (Exception ex)
    {
            Console.WriteLine("Fout: " + ex.Message);
    }
    finally
    {
            if (conn != null)
                    conn.Close();
    }
    ```

- **using-blok**:  
    Het `using`-blok zorgt ervoor dat een object (zoals een databaseverbinding) automatisch wordt opgeruimd als het blok klaar is, zelfs als er een fout optreedt. Dit is veiliger en korter dan handmatig sluiten in een `finally`.

    Voorbeeld:
    ```csharp
    using (var conn = new MySqlConnection(connStr))
    {
            try
            {
                    conn.Open();
                    // Code die de verbinding gebruikt
            }
            catch (Exception ex)
            {
                    Console.WriteLine("Fout: " + ex.Message);
            }
            // conn wordt hier automatisch gesloten
    }
    ```
---

## Stap 4: Gegevens uitlezen met een JOIN

Voorbeeld: Toon alle bestellingen met klantnaam en plantsoorten.

```csharp
string sql = @"
SELECT b.BestellingNr, k.Naam, p.Soortnaam, bp.Aantal
FROM Bestelling b
JOIN Klant k ON b.KlantNr = k.KlantNr
JOIN BestellingPlant bp ON b.BestellingNr = bp.BestellingNr
JOIN Plant p ON bp.PlantNr = p.PlantNr
ORDER BY b.BestellingNr;
";

using (var cmd = new MySqlCommand(sql, conn))
{
    try
    {
        using (var rdr = cmd.ExecuteReader())
        {
            while (rdr.Read())
            {
                Console.WriteLine($"Bestelling: {rdr["BestellingNr"]}, Klant: {rdr["Naam"]}, Plant: {rdr["Soortnaam"]}, Aantal: {rdr["Aantal"]}");
            }
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine("Fout bij uitlezen: " + ex.Message);
    }
}
```
### Uitleg over JOINS

Een **JOIN** in SQL combineert gegevens uit meerdere tabellen op basis van een gerelateerde kolom. In het voorbeeld hierboven worden de tabellen `Bestelling`, `Klant`, `BestellingPlant` en `Plant` samengevoegd. Hierdoor kun je in één query informatie ophalen over bestellingen, de bijbehorende klant en de planten die in die bestelling zitten.

**Hoe werkt de JOIN in het voorbeeld?**
- `JOIN Klant k ON b.KlantNr = k.KlantNr`: Voegt de klantgegevens toe aan elke bestelling.
- `JOIN BestellingPlant bp ON b.BestellingNr = bp.BestellingNr`: Voegt de planten (en aantallen) toe aan elke bestelling.
- `JOIN Plant p ON bp.PlantNr = p.PlantNr`: Voegt de soortnaam van de plant toe.

**Resultaat:**  
Elke rij in het resultaat bevat het bestelnummer, de klantnaam, de soortnaam van de plant en het aantal planten in die bestelling.

**Voorbeeld van een resultaat:**
```
Bestelling: 1, Klant: Jan Jansen, Plant: Ficus, Aantal: 2
Bestelling: 1, Klant: Jan Jansen, Plant: Monstera, Aantal: 1
Bestelling: 2, Klant: Piet Pieters, Plant: Monstera, Aantal: 3
...
```

Zo zie je in één overzicht welke klant welke planten heeft besteld en in welke aantallen.

## Parameterized Queries gebruiken

Bij het uitvoeren van SQL-queries in C# is het belangrijk om **parameterized queries** te gebruiken. Hiermee voorkom je SQL-injectie en zorg je ervoor dat gebruikersinvoer veilig verwerkt wordt.

### Waarom parameterized queries?

- **Beveiliging:** Voorkomt dat kwaadwillenden eigen SQL-code kunnen invoegen via gebruikersinvoer.
- **Betrouwbaarheid:** Voorkomt fouten bij speciale tekens (zoals quotes) in invoervelden.

### Voorbeeld zonder parameters (onveilig):

```csharp
string klantNaam = Console.ReadLine();
string sql = $"SELECT * FROM Klant WHERE Naam = '{klantNaam}'";
```

Dit is gevoelig voor SQL-injectie.

### Voorbeeld met parameters (veilig):

```csharp
string klantNaam = Console.ReadLine();
string sql = "SELECT * FROM Klant WHERE Naam = @naam";
using (var cmd = new MySqlCommand(sql, conn))
{
    cmd.Parameters.AddWithValue("@naam", klantNaam);
    using (var rdr = cmd.ExecuteReader())
    {
        while (rdr.Read())
        {
            Console.WriteLine($"KlantNr: {rdr["KlantNr"]}, Naam: {rdr["Naam"]}");
        }
    }
}
```

Gebruik altijd parameters bij het verwerken van invoer in je SQL-queries.
## Stap 5: Zelf uitbreiden

- Voeg functionaliteit toe om nieuwe klanten, planten of bestellingen toe te voegen.
- Maak een eenvoudige gebruikersinterface (optioneel).
- Experimenteer met verschillende JOINs en queries.

---

## Tips

- Gebruik altijd `try-catch`-blokken bij database-acties.
- Sluit verbindingen netjes af met `using`.
- Test je queries eerst in phpMyAdmin of MySQL Workbench.

---