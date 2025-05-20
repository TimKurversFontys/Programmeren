# Opdracht: Honden Onderzoeksdatabase Applicatie

## Doel
Ontwikkel een applicatie in C# waarbij studenten een database (SQL of NoSQL) gebruiken om onderzoeksdata over honden te beheren, met speciale focus op het vastleggen en analyseren van intelligentieonderzoek. De applicatie stelt gebruikers in staat om jarenlang verzamelde data over de intelligentie, groei en leefomstandigheden van honden te registreren, beheren en analyseren. Studenten leren zo werken met CRUD-operaties (Create, Read, Update, Delete), het opzetten van een datamodel en het uitvoeren van analyses op onderzoeksresultaten.

## Beschrijving
De "Honden Onderzoeksdatabase Applicatie" stelt gebruikers in staat om gegevens over honden, hun baasjes, voer, leefomstandigheden en onderzoeksresultaten te beheren. Alle gegevens worden opgeslagen en opgehaald uit een database. Studenten leren zo werken met CRUD-operaties (Create, Read, Update, Delete) en het opzetten van een datamodel.

## Functionaliteiten
1. **Honden Beheren**
    - Honden toevoegen, bekijken, aanpassen en verwijderen.
    - Elke hond heeft minimaal: Naam, Ras, Geboortejaar, Grootte, Intelligentiescore(s), Baasje.

2. **Baasjes Beheren**
    - Baasjes toevoegen, bekijken, aanpassen en verwijderen.
    - Elk baasje heeft minimaal: Naam, E-mailadres, Telefoonnummer.

3. **Voer en Leefomstandigheden**
    - Voer- en leefomstandigheden per hond vastleggen en beheren.
    - Denk aan: type voer, hoeveelheid, woonsituatie (bijvoorbeeld tuin, appartement), dagelijkse beweging.

4. **Onderzoeksresultaten Registreren**
    - Jaarlijkse testresultaten per hond toevoegen en beheren.
    - Resultaten bevatten: datum, type test, score, observaties.
    - Leg de ontwikkeling van de intelligentie van elke hond over meerdere jaren vast.

5. **Overzicht en Analyse**
    - Bekijk alle onderzoeksdata per hond, inclusief trends in intelligentie en groei.
    - Analyseer de invloed van voer, leefomstandigheden en baasje op de intelligentiescores.
    - Filter op baasje, ras, voer of leefomstandigheden.

6. **Zoeken en Filteren**
    - Zoek honden op naam of ras.
    - Filter onderzoeksresultaten op jaartal, baasje of andere relevante criteria.

## Mogelijk stappenplan
1. **1: Planning en Voorbereiding**

2. **2: Database Ontwerp**
    - Ontwerp het datamodel (tabellen/collecties en relaties).
    - Maak de database aan.

3. **3: Basisstructuur Applicatie**
    - Zet het C# project op (console, WinForms of ASP.NET).
    - Maak verbinding met de database.

4. **4: CRUD-functionaliteit**
    - Implementeer toevoegen, bekijken, aanpassen en verwijderen van honden, baasjes, voer en leefomstandigheden.

5. **5: Onderzoeksresultaten en Relaties**
    - Implementeer het toevoegen en beheren van onderzoeksresultaten en koppel deze aan honden.

6. **6: Overzichten en Analyse**
    - Maak overzichten van onderzoeksdata en implementeer zoek- en filterfunctionaliteit.

7. **7: Testen en Verbeteren**
    - Test de applicatie grondig.
    - Verbeter op basis van feedback.

8. **8: Presentatie en Reflectie**
    - Bereid een presentatie voor.
    - Reflecteer op het ontwikkelproces en de samenwerking.

## Extra Uitdagingen (optioneel)
- Implementeer gebruikersauthenticatie.
- Voeg rapportages toe (bijvoorbeeld gemiddelde intelligentiescore per ras).
- Gebruik Entity Framework of een andere ORM.

