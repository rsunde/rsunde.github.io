Nya versionen av C# är på väg så låt mig visa dig lite nyheter.

##### Auto-Properties

Här är ett exempel på hur man enklare kan fördefiniera värden.
```csharp
public class Kund
{
    public string FornamnV6 { get; set; } = "Gunnar";
    public string EfternamnV6 { get; } = "Gren";
    public string NamnV6 { get; }

    public string Fornamn { get; set; }
    public string Efternamn { get; private set; }

    public Kund()
    {
        NamnV6 = FornamnV6 + " " + EfternamnV6;

        Förnamn = "Gunnar";
        Efternamn = "Gren";
    }
}
```

Även om en property är private eller inte har en setter kan man ändå fördefiniera ett värde genom constructor.

##### Fat Arrow => Lambda Expression => Inline Function || Kalla det vad du vill =)

Nu kan man sätta en FAT ARROW på properties eller methods
```csharp
public class Kund
{
    public string FornamnV6 { get; set; } = "Gunnar";
    public string EfternamnV6 { get; } = "Gren";

    // Fat Arrows
    public string NamnV6 => FornamnV6 + " " + EfternamnV6;
    public void PrintNamnV6() => Console.WriteLine(FornamnV6 + " " + EfternamnV6);
    
    
    public string Fornamn { get; set; }
    public string Efternamn { get; private set; }

    // Gammal Uschj!!
    public string Namn()
    {
        return Fornamn + " " + Efternamn;
    }
    
    public void PrintNamn()
    {
        Console.WriteLine(Fornamn + " " + Efternamn);
    }
}
```

Som du kan se blir det lite mindre kod att skriva, men hur välanvänt det blir får vi se.

##### using static *
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
```csharp
int _kunder = kunder?.Length ?? 0;
int _ordrar = kunder?.Ordrar?.Count() ?? 0;
```

##### string Interpolation $
man brukar ju använda string.Format() för att formatera text och kunna placera variabler mitt i texten enkelt, men nu kan man i stället använda $ (nej pengar är inte lösningen) men nedan kan du se olika lösningar för att skriva ut formaterad text, gammalt med nytt, t.ex:
```csharp
string Fornamn = "Gunnar";
string Efternamn = "Gren";

// Välkommen till matchen Gunnar Gren!
Console.WriteLine($"Välkommen till matchen {Fornamn} {Efternamn}!");
Console.WriteLine(string.Format("Välkommen till matchen {0} {1}!", Fornamn, Efternamn));
Console.WriteLine("Välkommen till matchen " + Fornamn + " " + Efternamn + "!");

Console.WriteLine($"Ett plus ett = {1+1}"); // Ett plus ett = 2
```

Sen kan man tillochmed lägga in lite kod i {} hålet
```csharp
Fornamn = "Gunnar";
Efternamn = "Gren";

bool dag = false;

Console.WriteLine($"God {(dag ? "dag" : "kväll")} {Fornamn}."); // God kväll Gunnar.
```

##### Exception filter
Tydligen så fort man hamnar i ett catch{ ... } block så försvinner all information från stacken, genom att testa ett värde innan catch kan man välja att gå in i catch{ ... } blocket eller inte. Nedan visar jag nya jämfört med gamla.
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

Tydligen hade VB och F# detta innan, men vem programmerar i VB!?? =)
