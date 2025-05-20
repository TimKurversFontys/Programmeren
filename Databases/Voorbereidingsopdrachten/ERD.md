# Opdracht: Entity-Relationship Diagrams (ERD) Herhaling

## Doel
Oefen met het analyseren van scenario's en het omzetten van beschrijvingen naar een Entity-Relationship Diagram (ERD).

## Meer leren over ERD's

- [Wat is een Entity-Relationship Diagram? (dbdiagram.io)](https://dbdiagram.io/learn/er-diagram)
- [Entity-Relationship model (Wikipedia)](https://nl.wikipedia.org/wiki/Entity-relationshipmodel)
- [ERD Tutorial (Lucidchart)](https://www.lucidchart.com/pages/er-diagrams)
- [ERD uitleg en voorbeelden (Vertabelo)](https://vertabelo.com/blog/what-is-an-entity-relationship-diagram/)
- [ERD uitleg (Khan Academy, Engels)](https://www.khanacademy.org/computing/computer-programming/sql/relational-queries/a/relational-databases-entity-relationship-diagrams)

---

## Opdracht 1: Plantenkwekerij Systeem

### Scenario
Een plantenkwekerij wil haar voorraad en bestellingen bijhouden. Elke **Plant** heeft een uniek plantnummer, een soortnaam en een prijs per stuk. Elke **Klant** heeft een klantnummer, naam en contactgegevens. Klanten kunnen meerdere planten bestellen, en een bestelling kan meerdere planten bevatten. Van elke **Bestelling** worden de besteldatum en het aantal bestelde planten geregistreerd.

### Instructies
1. **Identificeer de entiteiten, attributen en relaties** uit het scenario.
2. **Teken een ERD** waarin je de entiteiten, hun attributen en de relaties (inclusief kardinaliteiten) weergeeft.
3. **Geef aan** welke attributen de primaire sleutels zijn.

---

## Opdracht 2: Minimalistisch Scenario

### Scenario
Op snelwegen worden voertuigen automatisch herkend via hun nummerbord. Elk voertuig kan op meerdere snelwegen worden gesignaleerd, en op elke snelweg kunnen meerdere voertuigen worden herkend.

### Instructies
1. **Bepaal zelf** welke entiteiten, attributen en relaties logisch zijn op basis van deze korte beschrijving.
2. **Teken een ERD** met minimaal twee entiteiten en hun relatie(s).
3. **Maak aannames** waar nodig en noteer deze kort onder je diagram.

---

## Extra Oefening

1. **Bedenk zelf een scenario** (bijvoorbeeld een webshop, school, sportclub) en schrijf een korte beschrijving.
2. **Maak een ERD** op basis van jouw scenario.

---

## Uitleg

- **Entiteit:** Een object of concept dat informatie bevat (bijv. Plant, Klant).
- **Attribuut:** Een eigenschap van een entiteit (bijv. soortnaam, naam).
- **Relatie:** Een verbinding tussen entiteiten (bijv. bestelt, wordt herkend op).
- **Kardinaliteit:** Geeft aan hoeveel instanties van de ene entiteit gekoppeld kunnen zijn aan instanties van een andere entiteit (bijv. één-op-veel).

