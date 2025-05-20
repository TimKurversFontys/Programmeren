# End-to-End (E2E) Testen met een Simpele C# Back-end en HTML/JavaScript Front-end

## Doel
In deze opdracht leer je hoe je een eenvoudige webapplicatie bouwt met een C#-back-end en een HTML/JavaScript-front-end. Vervolgens test je de werking van de applicatie met een E2E-testtool, zoals Playwright of Cypress.

## Opdracht 1: Maak een eenvoudige C# Web API

1. **Maak een nieuw ASP.NET Core Web API-project aan:**
    ```powershell
    dotnet new webapi -n SimpleApiDemo
    ```
2. **Voeg een eenvoudige controller toe (`Controllers/MessageController.cs`):**
    ```csharp
    using Microsoft.AspNetCore.Mvc;

    [ApiController]
    [Route("[controller]")]
    public class MessageController : ControllerBase
    {
        [HttpGet]
        public IActionResult Get()
        {
            return Ok(new { message = "Hallo van de back-end!" });
        }
    }
    ```
3. **Start de applicatie:**
    ```powershell
    dotnet run
    ```
    De API is nu bereikbaar op `https://localhost:5001/message` (of een andere poort).

## Opdracht 2: Maak een eenvoudige HTML/JavaScript Front-end

1. **Maak een nieuw bestand `index.html` aan in de root van je project:**
    ```html
    <!DOCTYPE html>
    <html lang="nl">
    <head>
        <meta charset="UTF-8">
        <title>SimpleApiDemo Front-end</title>
    </head>
    <body>
        <h1>Bericht van de server:</h1>
        <div id="message"></div>
        <script>
            fetch('https://localhost:5001/message')
                .then(response => response.json())
                .then(data => {
                    document.getElementById('message').innerText = data.message;
                })
                .catch(error => {
                    document.getElementById('message').innerText = 'Fout bij ophalen bericht';
                });
        </script>
    </body>
    </html>
    ```
2. **Open `index.html` in je browser.**  
   Je zou het bericht van de server moeten zien verschijnen.

## Opdracht 3: Schrijf een E2E-test

1. **Kies een E2E-testtool:**  
   Gebruik bijvoorbeeld [Playwright](https://playwright.dev/) of [Cypress](https://www.cypress.io/).
2. **Installeer de tool (voorbeeld met Playwright):**
    ```powershell
    npm init playwright@latest
    ```
3. **Maak een testbestand aan, bijvoorbeeld `e2e.spec.js`:**
    ```javascript
    const { test, expect } = require('@playwright/test');

    test('Bericht van de server wordt getoond', async ({ page }) => {
        await page.goto('file:///C:/pad/naar/index.html');
        const message = await page.locator('#message').innerText();
        expect(message).toContain('Hallo van de back-end');
    });
    ```
    > **Let op:** Voor lokale API-calls kan het nodig zijn CORS in je back-end toe te staan of de front-end via een lokale webserver te draaien.

4. **Voer de E2E-test uit:**  
   Volg de instructies van de gekozen tool om de test te draaien.

## Bonusopdracht

- Breid de API uit met een POST-endpoint en pas de front-end en E2E-test aan om ook het versturen van data te testen.

---

> **Tip:** Lees de documentatie van Playwright of Cypress voor meer voorbeelden van E2E-tests en best practices.