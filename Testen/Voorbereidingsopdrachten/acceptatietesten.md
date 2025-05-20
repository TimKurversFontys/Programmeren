# Acceptatietesten uitvoeren op een C#-applicatie

## Doel
In deze opdracht leer je hoe je acceptatietesten schrijft en uitvoert voor een C#-applicatie. Je ontdekt hoe je kunt controleren of de applicatie voldoet aan de gestelde eisen vanuit het perspectief van de eindgebruiker.

## Opdracht 1: Schrijf acceptatiecriteria

1. **Bepaal de functionaliteit:**  
    Kies een eenvoudige functionaliteit van een C#-consoleapplicatie, bijvoorbeeld een rekenmachine die optelt en aftrekt.
2. **Formuleer acceptatiecriteria:**  
    Beschrijf in duidelijke, meetbare punten wanneer de functionaliteit als “geaccepteerd” wordt beschouwd. Bijvoorbeeld:
    - De gebruiker kan twee getallen optellen.
    - De gebruiker krijgt het juiste resultaat te zien.
    - Bij ongeldige invoer krijgt de gebruiker een foutmelding.

## Opdracht 2: Schrijf acceptatietesten

1. **Kies een testframework:**  
    Gebruik bijvoorbeeld [SpecFlow](https://specflow.org/) (BDD voor .NET) of schrijf handmatig scenario’s in Gherkin-stijl.
2. **Maak een testproject aan:**  
    Voeg een nieuw testproject toe aan je oplossing, bijvoorbeeld met `dotnet new specflowproject -n Calculator.AcceptanceTests`.
3. **Schrijf scenario’s:**  
    Voeg een feature-bestand toe met scenario’s op basis van je acceptatiecriteria, bijvoorbeeld:

    ```gherkin
    Feature: Optellen van getallen

      Scenario: Twee positieve getallen optellen
         Given de gebruiker start de rekenmachine
         When de gebruiker voert 3 en 5 in en kiest voor optellen
         Then ziet de gebruiker het resultaat 8

      Scenario: Ongeldige invoer
         Given de gebruiker start de rekenmachine
         When de gebruiker voert "abc" en 5 in
         Then ziet de gebruiker een foutmelding
    ```

## Opdracht 3: Voer de acceptatietesten uit

1. **Implementeer de stappen:**  
    Koppel de scenario’s aan C#-stapdefinities en zorg dat ze de applicatie aanroepen.
2. **Voer de testen uit:**  
    Gebruik de test runner van je keuze (bijvoorbeeld Visual Studio Test Explorer of `dotnet test`) om de scenario’s uit te voeren.
3. **Bekijk de resultaten:**  
    Controleer of alle scenario’s slagen. Als een test faalt, verbeter dan de applicatie tot aan de acceptatiecriteria wordt voldaan.

## Bonusopdracht

Integreer de acceptatietesten in je CI/CD-pipeline, zodat bij elke wijziging automatisch gecontroleerd wordt of de applicatie nog aan de eisen voldoet.

---

> **Tip:** Werk samen met een (fictieve) opdrachtgever om de acceptatiecriteria zo realistisch mogelijk te maken.