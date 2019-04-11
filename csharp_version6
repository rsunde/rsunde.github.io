Nya versionen av C# är på väg så låt mig visa dig lite nyheter.

##### Auto-Properties

Här är ett exempel på hur man enklare kan fördefiniera värden.
<script src="https://gist.github.com/rsunde/e626c96f318e7bdbed7f.js"></script>
```csharp
public class Kund
{
    public string FörnamnV6 { get; set; } = "Gunnar";
    public string EfternamnV6 { get; } = "Gren";
    public string NamnV6 { get; }

    public string Förnamn { get; set; }
    public string Efternamn { get; private set; }

    public Kund()
    {
        NamnV6 = FörnamnV6 + " " + EfternamnV6;

        Förnamn = "Gunnar";
        Efternamn = "Gren";
    }
}
```

Även om en property är private eller inte har en setter kan man ändå fördefiniera ett värde genom constructor.

##### Fat Arrow => Lambda Expression => Inline Function || Kalla det vad du vill =)

Nu kan man sätta en FAT ARROW på properties eller methods
<script src="https://gist.github.com/rsunde/e5e3ea95fdce4dd1f01d.js"></script>
```csharp
public class Kund
{
    public string FörnamnV6 { get; set; } = "Gunnar";
    public string EfternamnV6 { get; } = "Gren";

    // Fat Arrows
    public string NamnV6 => FörnamnV6 + " " + EfternamnV6;
    public void PrintNamnV6() => Console.WriteLine(FörnamnV6 + " " + EfternamnV6);
    
    
    public string Förnamn { get; set; }
    public string Efternamn { get; private set; }

    // Gammal Uschj!!
    public string Namn()
    {
        return Förnamn + " " + Efternamn;
    }
    
    public void PrintNamn()
    {
        Console.WriteLine(Förnamn + " " + Efternamn);
    }
}
```

Som du kan se blir det lite mindre kod att skriva, men hur välanvänt det blir får vi se.

##### using static *
<script src="https://gist.github.com/rsunde/dd01c64dbd3bda9b2cfa.js"></script>
```csharp
using static System.Console;
using static System.Math;
using static System.DayOfWeek;

namespace SeeSharpVersionSixFeatures
{
    internal class Program
    {
        private static void Main(string[] args)
        {
            WriteLine(Sqrt(3*3 + 4*4));             
            WriteLine(Friday - Monday);
        }
    }
}
```

Som du kan se, genom att lägga in en using static så slipper man skriva ut hela klassen, eller enum.

##### null ?
Som du kanske vet så kan man deklarera variabler med ? så att dem får lov att vara null, t.ex:

**public int? nummer = null;**

men detta innebär en himla massa **if(nummer != null) { ... }** tester, vilket ifall man glömmer kolla kan skapa massa buggar!
så för att förenkla detta kan man nu slänga in ett frågetecken på det mesta.
<script src="https://gist.github.com/rsunde/bf0b80b66c98bf2e639f.js"></script>
```csharp
int _kunder = kunder?.Length ?? 0;
int _ordrar = kunder?.Ordrar?.Count() ?? 0;
```

##### string Interpolation $
man brukar ju använda string.Format() för att formatera text och kunna placera variabler mitt i texten enkelt, men nu kan man i stället använda $ (nej pengar är inte lösningen) men nedan kan du se olika lösningar för att skriva ut formaterad text, gammalt med nytt, t.ex:
<script src="https://gist.github.com/rsunde/c6624fb8d6d065fbcfea.js"></script>
```csharp
string Förnamn = "Gunnar";
string Efternamn = "Gren";

// Välkommen till matchen Gunnar Gren!
Console.WriteLine($"Välkommen till matchen {Förnamn} {Efternamn}!");
Console.WriteLine(string.Format("Välkommen till matchen {0} {1}!", Förnamn, Efternamn));
Console.WriteLine("Välkommen till matchen " + Förnamn + " " + Efternamn + "!");

Console.WriteLine($"Ett plus ett = {1+1}"); // Ett plus ett = 2
```

Sen kan man tillochmed lägga in lite kod i {} hålet
<script src="https://gist.github.com/rsunde/fe867a1f6b2e814669be.js"></script>
```csharp
Förnamn = "Gunnar";
Efternamn = "Gren";

bool dag = false;

Console.WriteLine($"God {(dag ? "dag" : "kväll")} {Förnamn}."); // God kväll Gunnar.
```

##### Exception filter
Tydligen så fort man hamnar i ett catch{ ... } block så försvinner all information från stacken, genom att att testa ett värde innan catch kan man välja att gå in i catch{ ... } blocket eller inte. Nedan visar jag nya jämfört med gamla.
<script src="https://gist.github.com/rsunde/d55ab11d7d6e1b9919eb.js"></script>
```csharp
public void Main()
{
  // New filters
  try
  {	
    throw new Exception("Test2");
  }
  catch(Exception ex) when(ex.Message == "Test1")
  {
    Console.WriteLine("Fångade Test 1");
  }
  catch(Exception ex) when(ex.Message == "Test2")
  {
    Console.WriteLine("Fångade Test 2");
  }
  
  // Old
  try
  {	
    throw new Exception("Test2");
  }
  catch(Exception ex)
  {
    if(ex.Message == "Test1")
    {
      Console.WriteLine("Fångade Test 1");
    }
    if(ex.Message == "Test2")
    {
      Console.WriteLine("Fångade Test 2");
    }  
  }
}
```

Tydligen hade VB och F# detta innan, men vem programmerar VB!?? =)
