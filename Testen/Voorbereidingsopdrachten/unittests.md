# Unit Tests schrijven in C#

## Doel
In deze opdracht leer je hoe je eenvoudige unit tests schrijft voor een bestaande applicatie in C#. Je gebruikt hiervoor de testbibliotheek MSTest.

## Opdracht 1: Testproject aanmaken

1. Maak een nieuw testproject aan in Visual Studio:
    - Kies voor een `MSTest Test Project`.
    - Voeg een referentie toe naar het project met je klassen (`Boek`, `Auteur`, etc.).

## Opdracht 2: Eenvoudige unit tests schrijven

Schrijf unit tests voor de klassen uit de onderstaande opdracht. Test bijvoorbeeld of het toevoegen van een auteur aan een boek correct werkt.

### Voorbeeld

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using System.Collections.Generic;

[TestClass]
public class BoekTests
{
    [TestMethod]
    public void BoekHeeftJuisteTitelNaAanmaken()
    {
        Boek boek = new Boek();
        boek.titel = "Testboek";
        Assert.AreEqual("Testboek", boek.titel);
    }

    [TestMethod]
    public void AuteurWordtToegevoegdAanBoek()
    {
        Boek boek = new Boek();
        Auteur auteur = new Auteur();
        auteur.naam = "Test Auteur";
        boek.auteurs.Add(auteur);

        Assert.AreEqual(1, boek.auteurs.Count);
        Assert.AreEqual("Test Auteur", boek.auteurs[0].naam);
    }

    [TestMethod]
    public void BoekWordtToegevoegdAanAuteur()
    {
        Boek boek = new Boek();
        boek.titel = "Testboek";
        Auteur auteur = new Auteur();
        auteur.boeken.Add(boek);

        Assert.AreEqual(1, auteur.boeken.Count);
        Assert.AreEqual("Testboek", auteur.boeken[0].titel);
    }
}
```
### Happy flow en het belang van goede testnamen

De bovenstaande tests laten de zogenaamde *happy flow* zien: ze testen of alles werkt zoals verwacht wanneer de invoer correct is. Dit is belangrijk, maar niet altijd voldoende. In de praktijk kunnen er ook onverwachte situaties optreden, zoals foutieve invoer of lege lijsten. Het is daarom verstandig om ook tests te schrijven voor deze *edge cases* of foutscenario's.

Daarnaast is het belangrijk om beschrijvende en lange testnamen te gebruiken. Zo is direct duidelijk wat een test controleert. Een goede testnaam beschrijft het scenario en het verwachte resultaat, bijvoorbeeld:  
`BoekToevoegenMetLegeTitel_GeeftFoutmelding`.

Dit helpt bij het snel begrijpen van testresultaten en het onderhouden van de codebase.

## Opdracht 3: Zelf tests schrijven

1. Schrijf minimaal drie eigen tests:
    - Test bijvoorbeeld of het ISBN goed wordt opgeslagen.
    - Test of een auteur meerdere boeken kan hebben.
    - Test of een boek meerdere auteurs kan hebben.

## Bonusopdracht

Schrijf een test voor de `Bibliotheek`-klasse (indien je deze hebt gemaakt). Test bijvoorbeeld of het zoeken op titel werkt.

---

> **Tip:** Gebruik de Test Explorer in Visual Studio om je tests uit te voeren en te bekijken of ze slagen.

## Vervolg: Integratietests opzetten

Naast unit tests zijn integratietests belangrijk om te controleren of verschillende onderdelen van je applicatie goed samenwerken. Waar een unit test één klasse of methode test, kijkt een integratietest naar het samenspel tussen meerdere klassen.

### Opdracht 4: Integratietestproject aanmaken

1. Maak een nieuw testproject aan, bijvoorbeeld `Bibliotheek.IntegrationTests`.
2. Voeg referenties toe naar de projecten die je wilt testen.

### Opdracht 5: Eenvoudige integratietest schrijven

Schrijf een integratietest waarin je bijvoorbeeld een `Boek` toevoegt aan een `Bibliotheek` en controleert of het boek daarna gevonden kan worden.

#### Voorbeeld

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public class BibliotheekIntegratieTests
{
    [TestMethod]
    public void BoekToevoegenEnZoekenWerkt()
    {
        Bibliotheek bibliotheek = new Bibliotheek();
        Boek boek = new Boek();
        boek.titel = "IntegratieTestBoek";
        bibliotheek.VoegBoekToe(boek);

        var gevondenBoek = bibliotheek.ZoekOpTitel("IntegratieTestBoek");
        Assert.IsNotNull(gevondenBoek);
        Assert.AreEqual("IntegratieTestBoek", gevondenBoek.titel);
    }
}
```

### Tips voor integratietests

- Zorg dat je testdata na elke test wordt opgeschoond.
- Gebruik duidelijke namen voor je integratietests, bijvoorbeeld:  
  `BoekToevoegenAanBibliotheek_BoekKanWordenGevonden`.
- Zorg dat niet alleen de happy flows getest worden.
- Integreer je integratietests in je buildproces zodat je altijd weet of alles samen blijft werken.

---