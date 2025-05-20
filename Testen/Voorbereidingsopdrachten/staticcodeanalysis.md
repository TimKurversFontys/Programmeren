# Statische Code Analyse gebruiken met SonarQube of SonarCloud

## Doel
In deze opdracht leer je hoe je statische code analyse toepast op een C#-project met behulp van SonarQube of SonarCloud. Je ontdekt hoe je codekwaliteit automatisch kunt controleren en verbeteren.

## Opdracht 1: SonarQube of SonarCloud instellen

1. **Kies een tool:**  
    Gebruik [SonarQube Community Edition](https://www.sonarqube.org/downloads/) (lokaal) of [SonarCloud](https://sonarcloud.io/) (cloud, gratis voor open source).
2. **Installeer SonarScanner:**  
    Volg de instructies op de website van SonarQube of SonarCloud om de SonarScanner te installeren.
3. **Maak een project aan:**  
    - Voor SonarQube: Maak een nieuw project aan in de webinterface.
    - Voor SonarCloud: Koppel je GitHub-repository en maak een project aan.

    ## Voorbeeldproject: C#-applicatie met veelvoorkomende codeproblemen

    Maak een nieuw C#-consoleproject aan, bijvoorbeeld met `dotnet new console -n StaticCodeAnalysisDemo`. Vervang de inhoud van `Program.cs` door onderstaande code. Deze code compileert, maar bevat diverse code smells en fouten die door statische analyse gevonden worden:

    ```csharp
    using System;
    using System.Collections.Generic;

    namespace StaticCodeAnalysisDemo
    {
        class Program
        {
            static void Main(string[] args)
            {
                var userList = new List<string>();
                userList.Add("Alice");
                userList.Add("Bob");
                userList.Add("Alice"); // Duplicate entry

                int unusedVariable = 42;

                foreach (var user in userList)
                {
                    if (user == "Bob")
                    {
                        Console.WriteLine("Hello Alice!"); // Wrong name
                    }
                }

                Console.WriteLine("Done");
            }

            // Unused method
            static void DoNothing()
            {
                int x = 0;
            }

            // Method with too many parameters
            static void ComplicatedMethod(int a, int b, int c, int d, int e, int f)
            {
                // No implementation
            }
        }
    }
    ```

    **Voorbeelden van problemen die statische analyse zal vinden:**
    - Ongebruikte variabelen en methoden
    - Foutieve of verwarrende naamgeving
    - Duplicatie in lijsten
    - Methoden met te veel parameters
    - Mogelijke bug in de `Console.WriteLine`-uitvoer

    Gebruik deze code als startpunt voor de analyse.

## Opdracht 2: Analyseer je C#-project

1. **Configureer het project:**  
    Voeg een `sonar-project.properties`-bestand toe aan de root van je project met minimaal:
    ```
    sonar.projectKey=JouwProjectNaam
    sonar.organization=JouwOrganisatie (alleen SonarCloud)
    sonar.host.url=http://localhost:9000 (voor SonarQube)
    sonar.login=JouwToken
    ```
2. **Voer de analyse uit:**  
    Open een terminal in de projectmap en voer uit:
    ```
    dotnet build
    sonar-scanner
    ```
3. **Bekijk de resultaten:**  
    Open de SonarQube- of SonarCloud-interface en bekijk de gevonden issues, code smells, duplicaties en test coverage.

## Opdracht 3: Verbeter je code

1. **Los minimaal drie gevonden issues op:**  
    - Bijvoorbeeld: verwijder ongebruikte variabelen, verbeter naamgeving, los mogelijke bugs op.
2. **Voer de analyse opnieuw uit** en controleer of de issues zijn opgelost.

## Bonusopdracht

Integreer SonarQube of SonarCloud in je CI/CD-pipeline (bijvoorbeeld GitHub Actions of Azure DevOps), zodat elke push automatisch wordt geanalyseerd.

---

> **Tip:** Lees de uitleg bij elk issue in SonarQube/SonarCloud om te begrijpen waarom het een probleem is en hoe je het kunt oplossen.