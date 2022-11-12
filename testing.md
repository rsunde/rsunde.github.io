# Osammanhängande Information Om Testning Inom Programmering
## TDD - Test Driven Development

### Varför är TDD bra?

Vad är det för skillnad mellan TDD och unit tests?

unit tests är en del av TDD, men TDD är inte unit tests.

Alla test exempel nedan har följande using(s):

```csharp
using MSTEST = Microsoft.VisualStudio.TestTools.UnitTesting;
using NUNIT = NUnit.Framework;
using XUNIT = Xunit;
using FluentAssertions;
using Shouldly;
```


**TDD** står för **T**est **D**riven **D**evelopment, vilket innebär att man skriver test kod innan man skriver själva koden.

För att skriva en kalkulator som lägger ihop två nummer skriver vi först test kod som ser ut på följande sätt:
```csharp
[Test]
public void CalculatorAddsTwoNumberPass()
{
  NUNIT.Assert.That(Calculator.Add(2, 2), Is.EqualTo(4));
}
```
när du sen kör detta testet så kommer en hel del saker att hända;

1. Calculator finns inte så vi måste skapa en class
2. Add() metoden måste sen också skapas
3. Nu kan du äntligen kompilera men testet är rött, så du börjar skriva sjävla koden i Add() metoden så ditt test blir grönt.

Och det är det som TDD går ut på, skriv kontrakt först och sen uppfyll kontraktet.

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

#### Nivå 1:
Här testas enbart methods i en class, t.ex du har en class Calculator med en Add() method
```csharp
[Test]
public void CalculatorAddsTwoNumberPass()
{
  NUNIT.Assert.That(Calculator.Add(2, 2), Is.EqualTo(4));
}
```

Väldigt enkelt att förstå och skriva.


#### Nivå 2:
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

  NUNIT.Assert.That(result[0], Is.EqualTo(3));
  NUNIT.Assert.That(result[1], Is.EqualTo(7));
  NUNIT.Assert.That(result[2], Is.EqualTo(11));
  
  NUNIT.Assert.That(calculator.Count(), Is.EqualTo(3));
}
```

Fortfarande enkelt att förstå och skriva, men test method är nästan större än koden i Calculator class.

#### Nivå 3:
Nu börjar det bli lite klurigt, vi behåller funktionaliteten från nivå 2, men instället för en intern array så sparar vi allt i en databas vilket innebär att vi har en dependency, denna dependency kan finnas på samma maskin, i samma project, och det kanske inte är speciellt svårt att använda den, men tänk om det är en extern webservice med inloggning och lösenord, detta kan vara väldigt långsamt, eller så kanske det inte funkar alls för din dator inte har tillgång till databasen eller internet.

#### Nivå 4:
Nu är det riktigt skumt, Vi behåller funktionaliteten från nivå 2, plus vi vill spara till en databas. Nivå 2 + Nivå 3.

### Test Ramverk

Vilka ramverk som finns och vad dem är bra eller dåliga på.

1. nUnit
2. xUnit
3. MSTest

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

Att tillägga är att det även finns specifika Assertion ramverk.

#### Attributes
Man måste beskriva en class eller function med ett attribute för att testmotorn skall veta vad den skall testa.

&nbsp;|NUnit|MSTest|xUnit
-|-|-|-
Class|[TestFixture]|[TestClass]|&nbsp;
Function (nullary)|[Test]|[TestMethod]|[Fact]
Function (n-ary)|&nbsp;|[DataTestMethod]|[Theory]
Function data|[TestCase(n-ary)]|[DataRow(n-ary)]|[InlineData(n-ary)]

https://en.wikipedia.org/wiki/Arity


Det finns även olika sätt att förbereda och avsluta test, man kan nyttja olika nivåer

&nbsp;|NUnit|MSTest|xUnit
-|-|-|-
Class|[OneTimeSetup]|[ClassInitialize]|IClassFixture<>
Method|[Setup]|[TestInitialize]|ctor
&nbsp;|NUnit|MSTest|xUnit
Class|[OneTimeTearDown]|[ClassCleanup]|IClassFixture<>
Method|[TearDown]|[TestCleanup]|IDisposable.Dispose


Ordning som de olika nivåerna körs vid 2 olika enhetstester:

&nbsp;|NUnit|MSTest|xUnit
-|-|-|-
1|OneTimeSetup|ClassInitialize|IClassFixture.ctor
2|Setup|TestSetup|ctor
3|Test1()|Test1()|Test1()
4|TearDown|TestCleanup|Dispose()
5|Setup|TestInitialize|ctor
6|Test2()|Test2()|Test2()
7|TearDown|TestCleanup|Dispose()
8|OneTimeTearDown|ClassCleanup|IClassFixture.Dispose()

Väldigt likt varandra, men xUnit kör en mer programspråk inriktad syntax över att använda attribut.


#### Asserts
Assert.* är alla test ramverks utgångspunk, men även här skriver man på lite olika sätt, nedan visas alla assert varianter samtidigt (detta gör man inte i verkligheten), FluentAssertions och Shouldly beskrivs i Assertion sektionen nedan;

```csharp
int expected = 0;
int actual = 4;

// NUnit have multiple assert metods, classic and fluent.
NUNIT.Assert.AreEqual(expected, actual);
NUNIT.Assert.That(actual, Is.EqualTo(expected));
        
MSTEST.Assert.AreEqual(expected, actual);
        
XUNIT.Assert.Equal(expected, actual);

actual.Should().Be(expected); // FluentAssertions

actual.ShouldBe(expected); // Shouldly
```

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
  NUNIT.Assert.That(something, Is.EqualTo(somethingElse));
}
```

### Assertion

Som beskrivs tidigare så har olika test ramverk olika sätt att skriva sina Assertions.

För att förenkla detta så finns det är även olika Assertion ramverk, och då försvinner anledningen till att välja ett specifikt test ramverk.


#### Assertion Ramverk

1. FluentAssertions
2. Shouldly

Exampel:

FluentAssertions:

```csharp
string actual = "ABCDEFGHI";

actual.Should()
  .StartWith("AB")
  .And.EndWith("HI")
  .And.Contain("EF")
  .And.HaveLength(9);

// or

actual.Should().StartWith("AB");
actual.Should().EndWith("HI");
actual.Should().Contain("EF");
actual.Should().HaveLength(9);  
```

Shouldly:

```csharp
string actual = "ABCDEFGHI";
actual.ShouldStartWith("AB");
actual.ShouldEndWith("HI");
actual.ShouldContain("EF");
actual.Length.ShouldBe(9);
```

båda ramverken har Match funktioner och väldigt liknande bas funktionalitet, men FluentAssertions har mer specifika Assert möjligheter och ser ut att vara mognare.


### Mocking
Mocking innebär att man lurar koden genom att skapa låtsas object som reagerar på olika saker och svarar på olika sätt, t.ex vill du inte att ditt test springer ut på internet och pratar med en extern tjänst, t.ex väder, så du "mockar" din egen väderservice i testkoden att ge dig ett svar du kan testa.

#### Mocking Ramverk

Finns ett gäng populära ramverk;

1. FakeItEasy
2. Moq
3. NSubstitute

Jag gillar ramverk som behåller någon slags C# känsla

Exempel:

FakeItEasy:

```csharp
// Creating a fake object is just dead easy!
// No mocks, no stubs, everything's a fake!
var lollipop = A.Fake<ICandy>();
var shop = A.Fake<ICandyShop>();

// Easily set up a call to return a value
A.CallTo(() => shop.GetTopSellingCandy()).Returns(lollipop);

// Use your fake as you would an instance of the faked type.
var developer = new SweetTooth();
developer.BuyTastiestCandy(shop);

// Asserting uses the same syntax as configuring calls.
// There's no need to learn another syntax.
A.CallTo(() => shop.BuyCandy(lollipop)).MustHaveHappened();
```

Moq:

```csharp
var mock = new Mock<IFoo>();
mock.Setup(foo => foo.DoSomething("ping")).Returns(true);

// access invocation arguments when returning a value
mock.Setup(x => x.DoSomethingStringy(It.IsAny<string>()))
		.Returns((string s) => s.ToLower());

// lazy evaluating return value
mock.Setup(foo => foo.GetCount()).Returns(() => 1);
```

NSubstitute:
```csharp
//Create:
var calculator = Substitute.For<ICalculator>();

//Set a return value:
calculator.Add(1, 2).Returns(3);
Assert.AreEqual(3, calculator.Add(1, 2));

//Check received calls:
calculator.Received().Add(1, Arg.Any<int>());
calculator.DidNotReceive().Add(2, 2);
```

... och det är NSubstitute som vinner.
