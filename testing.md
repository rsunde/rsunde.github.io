# Osammanhängande Information Om Testning Inom Programmering
## TDD - Test Driven Development

### Varför är TDD bra?

Vad är det för skillnad mellan TDD och unit tests?

unit tests är en del av TDD, men TDD är inte unit tests.

**TDD** står för **T**est **D**riven **D**evelopment, vilket innebär att man skriver test kod innan man skriver själva koden.

För att skriva en kalkulator som lägger ihop två nummer skriver vi först test kod som ser ut på följande sätt:
```csharp
[Test]
public void CalculatorAddsTwoNumberPass()
{
  NUnit.Framework.Assert.That(Calculator.Add(2, 2), Is.EqualTo(4));
}
```
när du sen kör detta testet så kommer en hel del saker att hända;

1. Calculator finns inte så vi måste skapa en class
2. Add() måste sen också skapas
3. Nu kan du äntligen kompilera men testen är röd, så du börjar skriva sjävla koden i Add() method så ditt test blir grönt.

Och det är det som TDD går ut på, skriv kontrakt först och sen uppfylla kontraktet, liknande när du skriver interfaces.

**Sammanfattning =)**

1. Skriv första testet
2. Skriv tillräckligt med kod så att testet blir grönt, t.ex hårdkoda samma värde som testas
3. Skriv ett test till med ett annat testvärde
4. Refaktorisera koden tills andra testet blir grönt och förhoppningsvis är även första testet grönt =)

```csharp
public static class Calculator
{
    static public int Add(int x, int y)
    {
        return x + y;
    }
}
```

Vad gör du om du redan har massa kod som inte har några tester?

Att ha tester innebär inte att koden är buggfri, så om allt funkar behöver du inte skriva massa tester, men det är bra att successivt lägga till tester så när eller om du behöver göra en refactor så vet du att du inte infört buggar.

Var kommer buggar ifrån om vi ändå har tester? kanske kontraktet är fel, eller för lite kunskap fanns innan, eller två olika methods som funkar buggfritt enskilt men funkar inte tillsammans.

Att hitta buggar gör man genom att använda slutprodukten.

Som du kan se i test method ovan så är test methods namn väldigt beskrivande vilket underlättar underhåll. 

### TDD Nivåer

**Nivå 1:**
Här testas enbart methods i en class, t.ex du har en class Calculator med en Add() method
```csharp
[Test]
public void CalculatorAddsTwoNumberPass()
{
  NUnit.Framework.Assert.That(Calculator.Add(2, 2), Is.EqualTo(4));
}
```

Väldigt enkelt att förstå och skriva.


**Nivå 2:**
Här testas ett object av en class, t.ex du har fortfarande din Calculator class, men varje gång du använt Add() så sparar du resultat i en intern array och du har lagt till en ny method som räknar storleken på din interna array.
```csharp
[Test]
public void Calculator3AddOperationsThenCount()
{
  var calculator = new Calculator();
 
  calculator.Add(1, 2);
  calculator.Add(3, 4);
  calculator.Add(5, 6);
 
  var result = calculator.GetHistory();

  NUnit.Framework.Assert.That(result[0], Is.EqualTo(3));
  NUnit.Framework.Assert.That(result[1], Is.EqualTo(7));
  NUnit.Framework.Assert.That(result[2], Is.EqualTo(11));
  
  NUnit.Framework.Assert.That(calculator.Count(), Is.EqualTo(3));
}
```

Fortfarande enkelt att förstå och skriva, men test method är nästan större än koden i Calculator class.

**Nivå 3:**
Nu börjar det bli lite klurigt, vi behåller funktionaliteten från nivå 2, men instället för en intern array så sparar vi allt i en databas vilket innebär att vi har en dependency, denna dependency kan finnas på samma maskin, i samma project, och det kanske inte är speciellt svårt att använda den, men tänk om det är en extern webservice med inloggning och lösenord, detta kan vara väldigt långsamt, eller så kanske det inte funkar alls för din dator inte har tillgång till databasen eller internet.

**Nivå 4:**
Nu är det riktigt skumt, Vi behåller funktionaliteten från nivå 2, plus vi vill spara till en databas. Nivå 2 + Nivå 3.


### Mocking
Lämnad tom för jag har ingen lust =)

### Test Ramverk

Vilka ramverk som finns och vad dem är bra eller dåliga på.

1. nUnit
2. xUnit
3. MSTest

från min forskning verkar det vara att nUnit och xUnit är bättre än MSTest, så jag beslutade mig för att koncentrera mig på nUnit och xUnit då dem är väldigt lika, får återkomma till MSTest en annan vacker dag.

Exempel:

Class som skall testas
```csharp
public static class Calculator
{
    static public int Add(int x, int y)
    {
        return x + y;
    }
}
```

### "Språk"-val
De olika test ramverken använder olika "språk" för att beskriva saker i ramverket.

Nedan kommer jag beskriva de olika sätten som man valt att skriva kod på, med andra ord, när man skriver kod så finns det ändå olika sätt att kalla en funktion, eller ett attribute, etc etc. och vad som känns rätt när man läser eller skriver koden tycker jag är viktigt, speciellt nu när det finns olika att välja mellan.. välj den som känns rätt.

#### Attributes
Man måste beskriva en class eller function med ett attribute för att testmotorn skall veta vad den skall testa.

&nbsp;|xUnit|NUnit|MsTest
-|-|-|-
Class|&nbsp;|[TestFixture]|[TestClass]
Function (nullary)|[Fact]|[Test]|[TestMethod]
Function (n-ary)|[Theory]|&nbsp;|[DataTestMethod]
Function data|[InlineData(n-ary)]|[TestCase(n-ary)]|[DataRow(n-ary)]

https://en.wikipedia.org/wiki/Arity

#### Asserts
Assert.* är alla test ramverks utgångspunk, men även här skriver man på lite olika sätt;

**xUnit**
-

**nUnit**
-

**MSTest**
- AreEqual()
- AreNotEqual()
- AreSame()
- AreNotSame()
- IsXxxx()
- IsNotXxxx()


När man använder NUnit kan man skriva samma test på två olik sätt
```csharp

// Constraint Model
[Test]
public void CalculatorAddsTwoNumberPass()
{
  var somethingElse = 4;
  var something = Calculator.Add(2, 2);
  
  NUnit.Framework.Assert.That(something, Is.EqualTo(somethingElse));
}

// Classic Model
[Test]
public void CalculatorAddsTwoNumberPass()
{
  var expected = 4;
  var result = Calculator.Add(2, 2);

  NUnit.Framework.Assert.AreEqual(expected, result);
}
```

jag föredrar nog att skriva .That() som är det nya sättet istället för den klassiska stilen IsEqual().

När man skriver ett test så brukar man dela upp testet i olika steg, man kan välja att kommentera fram sektionerna, men detta kan kännas onödigt när koden skall vara självbeskrivande, men nedan följer ett exemple på **The AAA (Arrange, Act, Assert) pattern**...

```csharp

// Constraint Model
[Test]
public void CalculatorAddsTwoNumberPass()
{
  // Arrange
  var somethingElse = 4;
  
  // Act
  var something = Calculator.Add(2, 2);
  
  // Assert
  NUnit.Framework.Assert.That(something, Is.EqualTo(somethingElse));
}
```


Och här är två tester med samma kod en för nUnit och en för xUnit


här är även samma test kod för nUnit fast skrivet på det klassiska sättet


notera även att i xUnit är .Are borttaget så .AreEqual() blir .Equal()
