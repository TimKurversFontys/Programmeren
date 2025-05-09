# Constructoren en Encapsulatie

In deze opdracht bouwen we voort op de voorkennis uit **Klassen en Objecten**. We introduceren het concept **encapsulatie** en laten zien hoe dit kan worden toegepast in een voorbeeld met bankrekeningen.

## Probleem: Geen Encapsulatie

Laten we beginnen met een eenvoudige implementatie van een `Bankrekening`-klasse zonder enige vorm van encapsulatie:

```csharp
public class Bankrekening
{
    public string Eigenaar;
    public decimal Saldo;
}
```

Met deze implementatie kunnen we direct de velden van een `Bankrekening`-object aanpassen, wat ongewenst gedrag kan veroorzaken:

```csharp
Bankrekening rekening1 = new Bankrekening();
rekening1.Eigenaar = "Jan";
rekening1.Saldo = 1000m;

Bankrekening rekening2 = new Bankrekening();
rekening2.Eigenaar = "Piet";
rekening2.Saldo = 500m;

// Ongewenst: Direct aanpassen van saldo
rekening1.Saldo = rekening2.Saldo;
```

Hierdoor kan het saldo van `rekening1` zomaar worden overschreven, wat niet wenselijk is.

## Oplossing: Velden Private Maken

Om dit probleem op te lossen, maken we de velden `private`. Hierdoor kunnen ze niet meer direct van buiten de klasse worden aangepast:

```csharp
public class Bankrekening
{
    private string eigenaar;
    private decimal saldo;
}
```

Hoewel dit voorkomt dat de velden direct worden aangepast, ontstaan er nu problemen omdat we geen manier meer hebben om de waarden van `eigenaar` en `saldo` in te stellen of op te vragen.

## Constructoren Introduceren

Om dit probleem op te lossen, introduceren we een **constructor**. Hiermee kunnen we de initiële waarden van de velden instellen bij het aanmaken van een object:

```csharp
public class Bankrekening
{
    private string eigenaar;
    private decimal saldo;

    public Bankrekening(string eigenaar, decimal startSaldo)
    {
        this.eigenaar = eigenaar;
        this.saldo = startSaldo;
    }
}
```

Nu kunnen we een `Bankrekening`-object aanmaken met een eigenaar en een startsaldo:

```csharp
Bankrekening rekening = new Bankrekening("Jan", 1000m);
```

## Getters en Setters

Om toegang te krijgen tot de velden, voegen we **getters** en **setters** toe:

```csharp
public class Bankrekening
{
    private string eigenaar;
    private decimal saldo;

    public Bankrekening(string eigenaar, decimal startSaldo)
    {
        this.eigenaar = eigenaar;
        this.saldo = startSaldo;
    }

    public string GetEigenaar()
    {
        return eigenaar;
    }

    public decimal GetSaldo()
    {
        return saldo;
    }

    public void SetSaldo(decimal nieuwSaldo)
    {
        if (nieuwSaldo >= 0)
        {
            saldo = nieuwSaldo;
        }
    }
}
```

Met deze methoden kunnen we de waarden veilig opvragen en aanpassen:

```csharp
Bankrekening rekening = new Bankrekening("Jan", 1000m);
Console.WriteLine(rekening.GetSaldo()); // Output: 1000
rekening.SetSaldo(1200m);
Console.WriteLine(rekening.GetSaldo()); // Output: 1200
```

## Properties

Een modernere en meer compacte manier om getters en setters te implementeren is door gebruik te maken van **properties**:

```csharp
public class Bankrekening
{
    public string Eigenaar { get; private set; }
    public decimal Saldo { get; private set; }

    public Bankrekening(string eigenaar, decimal startSaldo)
    {
        Eigenaar = eigenaar;
        Saldo = startSaldo;
    }

    public void Stort(decimal bedrag)
    {
        if (bedrag > 0)
        {
            Saldo += bedrag;
        }
    }

    public void NeemOp(decimal bedrag)
    {
        if (bedrag > 0 && bedrag <= Saldo)
        {
            Saldo -= bedrag;
        }
    }
}
```

Met properties kunnen we nu veilig de waarden van `Eigenaar` en `Saldo` opvragen, terwijl we controle houden over hoe ze worden aangepast.

```csharp
Bankrekening rekening = new Bankrekening("Jan", 1000m);
rekening.Stort(500m);
rekening.NeemOp(200m);
Console.WriteLine(rekening.Saldo); // Output: 1300
```

## Conclusie

Door gebruik te maken van encapsulatie met private velden, constructoren, getters, setters en properties, kunnen we de interne staat van een klasse beschermen en ongewenst gedrag voorkomen. Dit is een belangrijk concept in objectgeoriënteerd programmeren.