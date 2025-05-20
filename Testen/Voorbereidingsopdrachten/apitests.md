# API Testen met ASP.NET Core en Postman

## Doel
In deze opdracht leer je hoe je een eenvoudige API maakt met ASP.NET Core en hoe je deze test met Postman of een gratis alternatief zoals [Hoppscotch](https://hoppscotch.io/).

## Opdracht 1: Maak een eenvoudige API

1. **Nieuw project aanmaken:**  
    Open een terminal en voer uit:
    ```
    dotnet new webapi -n BasicApiDemo
    cd BasicApiDemo
    ```

2. **Voeg een eenvoudige controller toe:**  
    Maak een bestand `Controllers/GreetingController.cs` met de volgende inhoud:
    ```csharp
    using Microsoft.AspNetCore.Mvc;

    namespace BasicApiDemo.Controllers
    {
         [ApiController]
         [Route("[controller]")]
         public class GreetingController : ControllerBase
         {
              [HttpGet]
              public IActionResult GetGreeting()
              {
                    return Ok("Hallo, dit is een API!");
              }
         }
    }
    ```

3. **Start de applicatie:**  
    ```
    dotnet run
    ```
    De API draait nu op `https://localhost:5001` (of een andere poort).

## Opdracht 2: Test de API met Postman of Hoppscotch

1. **Installeer Postman:**  
    Download en installeer [Postman](https://www.postman.com/downloads/) of gebruik [Hoppscotch](https://hoppscotch.io/).

2. **Stuur een GET-request:**  
    - URL: `https://localhost:5001/greeting`
    - Methode: `GET`
    - Klik op "Send".

3. **Bekijk het antwoord:**  
    Je zou als antwoord `"Hallo, dit is een API!"` moeten zien.

## Opdracht 3: Experimenteer

1. **Pas het antwoord aan:**  
    Verander de tekst in de controller en test opnieuw.
2. **Voeg een nieuwe endpoint toe:**  
    Voeg bijvoorbeeld een endpoint toe dat je naam als parameter accepteert en een persoonlijke begroeting teruggeeft.

    ```csharp
    [HttpGet("{name}")]
    public IActionResult GetPersonalGreeting(string name)
    {
         return Ok($"Hallo, {name}!");
    }
    ```
    Test deze met `/greeting/Tim`.

---

> **Tip:** Je kunt ook andere gratis API-testtools gebruiken, zoals [Insomnia](https://insomnia.rest/) of [curl](https://curl.se/).
