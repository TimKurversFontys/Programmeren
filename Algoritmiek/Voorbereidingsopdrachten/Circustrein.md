## Opdracht: Dieren verdelen over de circustrein

De circustrein staat voor de uitdaging om een reeks circusdieren veilig en efficiënt over de wagons te verdelen. Hierbij moet rekening gehouden worden met:

- **Diermaten:** klein (1), middelgroot (3), groot (5)
- **Dieet:** herbivoor of carnivoor
- **Wagoncapaciteit:** maximaal 10 maatpunten per wagon

### Eisen en beperkingen

- Carnivoren mogen niet samen met andere carnivoren of herbivoren in een wagon geplaatst worden als ze deze kunnen opeten (zelfde maat of kleiner).
- De totale maat van de dieren in een wagon mag niet boven de 10 uitkomen.

### Algoritmische aanpak

Om de dieren te verdelen, kun je gebruik maken van bekende algoritmen voor het verdelen van objecten over containers, zoals het **bin packing problem**. Twee veelgebruikte strategieën zijn:

- **First Fit:** Plaats elk dier in de eerste wagon waar het past en veilig is.
- **Best Fit:** Plaats elk dier in de wagon waar het het beste past (minst overgebleven ruimte), zolang het veilig is.

Beide strategieën moeten uitgebreid worden met controles op dieet en veiligheid.

### Big O Notatie

- **First Fit:** O(n·m), waarbij n het aantal dieren is en m het aantal wagons.
- **Best Fit:** O(n·m), omdat voor elk dier alle wagons gecontroleerd moeten worden.

### Uitdaging

Implementeer een algoritme dat bovenstaande eisen respecteert en gebruik maakt van First Fit of Best Fit. Experimenteer met beide strategieën en vergelijk het aantal benodigde wagons en de efficiëntie.
