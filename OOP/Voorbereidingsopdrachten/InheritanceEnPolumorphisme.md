# Inheritance en Polymorphisme
We introduceren nu de concepten **inheritance** (overerving) en **polymorphisme**.

## Wat is Inheritance?

Inheritance is een fundamenteel concept in objectgeoriënteerd programmeren (OOP). Het stelt een klasse in staat om eigenschappen en methoden van een andere klasse over te nemen. Dit bevordert hergebruik van code en maakt het mogelijk om hiërarchieën van klassen te creëren.

### Voorbeeld:
```csharp
// Superklasse
class Dier
{
    public string Naam { get; set; }

    public virtual void MaakGeluid()
    {
        Console.WriteLine("Dit dier maakt een geluid.");
    }
}

// Subklasse
class Hond : Dier
{
    public override void MaakGeluid()
    {
        Console.WriteLine("Woef woef!");
    }
}
```

In dit voorbeeld erft de klasse `Hond` de eigenschappen en methoden van de klasse `Dier`. De methode `MaakGeluid` wordt echter overschreven in de subklasse.

---

## Wat is Polymorphisme?

Polymorphisme betekent "veelvormigheid" en verwijst naar het vermogen van verschillende objecten om op dezelfde methode-aanroep verschillend te reageren. Dit wordt vaak bereikt door method-overriding.

### Voorbeeld:
```csharp
class Kat : Dier
{
    public override void MaakGeluid()
    {
        Console.WriteLine("Miauw!");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Dier mijnDier = new Hond();
        mijnDier.MaakGeluid(); // Output: Woef woef!

        mijnDier = new Kat();
        mijnDier.MaakGeluid(); // Output: Miauw!
    }
}
```

Hier zien we dat de methode `MaakGeluid` afhankelijk van het type object een andere uitvoer geeft, ondanks dat de methode wordt aangeroepen via een referentie van het type `Dier`.

---

## Belang van Inheritance en Polymorphisme

- **Codehergebruik**: Door inheritance kunnen we gemeenschappelijke functionaliteit in een superklasse definiëren en hergebruiken in subklassen.
- **Flexibiliteit**: Polymorphisme maakt het mogelijk om generieke code te schrijven die met verschillende typen objecten kan werken.
- **Onderhoudbaarheid**: Door hiërarchieën en polymorfe methoden wordt de code overzichtelijker en eenvoudiger te onderhouden.

---
## Opdracht: Werken met Inheritance

### Doel:
Oefen met het toepassen van inheritance door een hiërarchie van klassen te maken en methoden te overschrijven.

### Opdrachtbeschrijving:
1. Maak een superklasse genaamd `Voertuig` met de volgende eigenschappen en methoden:
    - Eigenschap: `Snelheid` (int)
    - Methode: `Rijd()` die de tekst "Het voertuig rijdt." naar de console schrijft.

2. Maak twee subklassen genaamd `Auto` en `Fiets` die erven van `Voertuig`.
    - Overschrijf de methode `Rijd()` in beide klassen:
      - Voor `Auto`: Schrijf "De auto rijdt met een snelheid van X km/u." naar de console, waarbij X de waarde van `Snelheid` is.
      - Voor `Fiets`: Schrijf "De fiets rijdt met een snelheid van X km/u." naar de console, waarbij X de waarde van `Snelheid` is.

3. Maak een `Program`-klasse met een `Main`-methode waarin je het volgende doet:
    - Maak een object van `Auto` en stel de snelheid in op 120.
    - Maak een object van `Fiets` en stel de snelheid in op 25.
    - Roep de methode `Rijd()` aan voor beide objecten.

### Verwachte Output:
```plaintext
De auto rijdt met een snelheid van 120 km/u.
De fiets rijdt met een snelheid van 25 km/u.
```

### Uitdagende oefening:
Voeg een extra subklasse toe genaamd `Vliegtuig` en overschrijf de methode `Rijd()` om "Het vliegtuig vliegt met een snelheid van X km/u." te schrijven. Pas de `Main`-methode aan om ook een object van `Vliegtuig` te maken en de methode `Rijd()` aan te roepen.

