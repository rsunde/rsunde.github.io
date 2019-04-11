+ **static**
+ **abstract**
    *   denna metoden kan inte ha någon kod utan skrivs enbart som kontrakt för andra klasser som ärver från denna klassen och måste implementera metoden, **override** måste användas för att implementera denna metoden.
    *   för att använda ***abstract*** på en metod måste klassen också vara ***abstract*** vilket innebär att man måste skriva en annan klass som ärver från den ***abstract*** klassen.
+ **virtual**
    *   denna metoden kan bytas ut med **override** när klassen ärvs.
+ **override**
    *   byter ut ärvd **virtual** metod, så om ett objekt packas upp behålls denna metoden.
+ **new**
    *   gömmer ärvd metod, om objekt packas upp förlorar man denna metoden.

***du får ursäkta röran nedanför, var ett tappert försök att skapa tabeller med markdown.***

<table><tr><td>Class A
virtual One();
Two();
ThreeA();</td>
    <td>Class B : A
override One();
new Two();
ThreeB();</td>
  </tr><tr><td></td>
    <td>en klass som ärver från en annan klass kan definiera om metoder med samma namn, om inga keywords används blir det automagiskt new, men man bör skriva new så det inte finns några oklarheter</td>
  </tr></table><table><tr><td>var a = new A();
a.One();
a.Two();
a.ThreeA();</td>
    <td>var b = new B();
b.One();
b.Two();
b.ThreeB();
b.ThreeA();
</td>
    <td>var c = (A) b;
b.One();
a.Two();
a.ThreeA();</td>
  </tr><tr><td>a objekt från A klass har sina A metoder</td>
    <td>b objekt från B klass har sina B metoder men ärver även metoder från A klass</td>
    <td>b object packas upp till a objekt, efterssom B klass har override på One() stannar den kvar även om nya objektet är från A klass</td>
  </tr></table>
|**Class A**   |**Class B : A**|
|virtual One();|override One();|
|Two();        |new Two();     |

<table><thead><tr><th>ThreeA();</th><th>ThreeB();</th></tr></thead><tbody><tr><td></td><td>en klass som ärver från en annan klass kan definiera om metoder med samma namn, om inga keywords används blir det automagiskt new, men man bör skriva new så det inte finns några oklarheter</td></tr></tbody></table>

|var a = new A();|var b = new B();|var c = (A) b;|
|a.One();        |b.One();        |b.One();      |
|a.Two();        |b.Two();        |a.Two();      |
|a.ThreeA();     |b.ThreeB();     |a.ThreeA();   |

<table><thead><tr><th></th><th>b.ThreeA();</th><th></th></tr></thead><tbody><tr><td>a objekt från A klass har sina A metoder</td><td>b objekt från B klass har sina B metoder men ärver även metoder från A klass</td><td>b object packas upp till a objekt, efterssom B klass har override på One() stannar den kvar även om nya objektet är från A klass</td></tr></tbody></table>
