# UML, Klassen en Objecten

## Doel
In deze opdracht maak je kennis met de basisprincipes van UML-klassendiagrammen, klassen en objecten. Je leert hoe je een klassendiagram opstelt en hoe je dit vertaalt naar code.

## Opdracht 1: Klassendiagram maken

1. Stel je voor dat je een systeem bouwt voor een bibliotheek. Het systeem moet informatie bijhouden over boeken en auteurs.
2. Maak een UML-klassendiagram waarin je de volgende klassen definieert:
    - **Boek**: met attributen zoals `titel` (string), `ISBN` (string) en `aantalPaginas` (integer).
    - **Auteur**: met attributen zoals `naam` (string) en `geboortejaar` (integer).
3. Geef de relatie tussen de klassen weer:
    - Een boek kan meerdere auteurs hebben.
    - Een auteur kan meerdere boeken geschreven hebben.

Teken het diagram op papier of gebruik een online tool zoals [Lucidchart](https://www.lucidchart.com) of [Draw.io](https://app.diagrams.net).

## Opdracht 2: Klassen implementeren

Schrijf de klassen in C# op basis van het UML-klassendiagram dat je hebt gemaakt. Gebruik public fields in plaats van properties of constructoren.

### Voorbeeld
```csharp
using System;
using System.Collections.Generic;

class Boek
{
    public string titel;
    public string ISBN;
    public int aantalPaginas;
    public List<Auteur> auteurs = new List<Auteur>();
}

class Auteur
{
    public string naam;
    public int geboortejaar;
    public List<Boek> boeken = new List<Boek>();
}
```

## Opdracht 3: Objecten maken

1. Maak een object van de klasse `Boek` met de titel "De Ontdekking van de Hemel", ISBN "9789023467443" en 900 pagina's.
2. Maak twee objecten van de klasse `Auteur`:
    - Harry Mulisch, geboren in 1927.
    - Een fictieve co-auteur, bijvoorbeeld "Jan Jansen", geboren in 1980.
3. Voeg de auteurs toe aan het boek en voeg het boek toe aan de lijst van boeken van beide auteurs.

### Voorbeeld
```csharp
Boek boek = new Boek();
boek.titel = "De Ontdekking van de Hemel";
boek.ISBN = "9789023467443";
boek.aantalPaginas = 900;

Auteur auteur1 = new Auteur();
auteur1.naam = "Harry Mulisch";
auteur1.geboortejaar = 1927;

Auteur auteur2 = new Auteur();
auteur2.naam = "Jan Jansen";
auteur2.geboortejaar = 1980;

boek.auteurs.Add(auteur1);
boek.auteurs.Add(auteur2);

auteur1.boeken.Add(boek);
auteur2.boeken.Add(boek);
```

## Opdracht 4: Output genereren

Schrijf een methode die de details van een boek en zijn auteurs print. Bijvoorbeeld:
```plaintext
Titel: De Ontdekking van de Hemel
ISBN: 9789023467443
Aantal pagina's: 900
Auteurs:
- Harry Mulisch (1927)
- Jan Jansen (1980)
```

### Voorbeeld
```csharp
void PrintBoekDetails(Boek boek)
{
    Console.WriteLine($"Titel: {boek.titel}");
    Console.WriteLine($"ISBN: {boek.ISBN}");
    Console.WriteLine($"Aantal pagina's: {boek.aantalPaginas}");
    Console.WriteLine("Auteurs:");
    foreach (Auteur auteur in boek.auteurs)
    {
        Console.WriteLine($"- {auteur.naam} ({auteur.geboortejaar})");
    }
}

PrintBoekDetails(boek);
```

## Bonusopdracht

Breid het systeem uit met een klasse `Bibliotheek`. Deze klasse moet een lijst van boeken bevatten en methoden om boeken toe te voegen en te zoeken op titel.
