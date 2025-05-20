# CI/CD Pipeline opzetten met GitHub Actions

## Doel
In deze opdracht leer je hoe je een eenvoudige CI/CD-pipeline opzet voor een C#-project met behulp van GitHub Actions. Je ontdekt hoe je automatisch builds en tests uitvoert bij elke push naar je repository.

## Opdracht 1: GitHub Actions Workflow aanmaken

1. **Fork of maak een nieuw C#-project:**  
    Maak een nieuw repository aan op GitHub met een C#-consoleapplicatie, bijvoorbeeld via `dotnet new console -n CiCdDemo`.

2. **Voeg een workflow toe:**  
    Maak in je repository de map `.github/workflows` aan en voeg een bestand toe, bijvoorbeeld `ci.yml`, met de volgende inhoud:

    ```yaml
    name: .NET Build & Test

    on:
      push:
         branches: [ main ]
      pull_request:
         branches: [ main ]

    jobs:
      build:
         runs-on: ubuntu-latest

         steps:
            - uses: actions/checkout@v4
            - name: Setup .NET
              uses: actions/setup-dotnet@v4
              with:
                 dotnet-version: '8.0.x'
            - name: Restore dependencies
              run: dotnet restore
            - name: Build
              run: dotnet build --no-restore --configuration Release
            - name: Test
              run: dotnet test --no-build --verbosity normal
    ```

3. **Commit en push:**  
    Commit en push je wijzigingen naar GitHub. Bekijk onder het tabblad 'Actions' of de workflow automatisch wordt uitgevoerd.

## Opdracht 2: Workflow uitbreiden

1. **Voeg een badge toe aan je README:**  
    Voeg bovenaan je `README.md` het volgende toe om de buildstatus te tonen:

    ```markdown
    ![Build Status](https://github.com/<jouw-gebruikersnaam>/<jouw-repo>/actions/workflows/ci.yml/badge.svg)
    ```

2. **Voeg een stap toe voor codeanalyse:**  
    Voeg in de workflow een extra stap toe na het builden, bijvoorbeeld:

    ```yaml
    - name: Code Analysis
      run: dotnet format --verify-no-changes
    ```

## Opdracht 3: Automatisch deployen (optioneel)

1. **(Bonus) Voeg een stap toe om te deployen:**  
    Bijvoorbeeld: publiceer een build-artifact of deploy naar Azure (gebruik hiervoor de officiële GitHub Actions).

---

> **Tip:** Bekijk de logs van elke workflow-run om te zien waar het eventueel misgaat en hoe je dit kunt oplossen.