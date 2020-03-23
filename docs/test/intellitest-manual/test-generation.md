---
title: Generování zkoušek | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c251a1539b42da2b4e92c2996457075f3c3be135
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302607"
---
# <a name="test-generation"></a>Generování testů

Při tradičním testování částí se zkouška skládá z několika věcí:

* [Posloupnost volání metod](test-generation.md#test-generators)
* Argumenty, s nimiž jsou volány metody; argumenty jsou [testovací vstupy](input-generation.md)
* Ověření zamýšleného chování testované aplikace uvedením sady [kontrolních výrazů](#assumptions-and-assertions)

Následuje příklad zkušební struktury:

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

IntelliTest může často automaticky určit příslušné hodnoty argumentů pro obecnější [parametrizované jednotkové testy](#parameterized-unit-testing), které poskytují posloupnost volání metod a kontrolních výrazů.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generátory testů

IntelliTest generuje testovacích případů výběrem posloupnosti metod implementace testované provést a potom generování vstupů pro metody při kontrole kontrolní výrazy nad odvozená data.

[Parametrizovaný test částí](#parameterized-unit-testing) přímo uvádí posloupnost volání metody v jeho těle.

Když IntelliTest potřebuje vytvořit objekty, volání konstruktory a metody výroby budou automaticky přidány do sekvence podle potřeby.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametrizované testování částí

*Parametrizované testy jednotek* (PUT) jsou testy, které berou parametry. Na rozdíl od tradičních testů částí, které jsou obvykle uzavřené metody, PUTs trvat libovolnou sadu parametrů. Je to tak jednoduché? Ano - odtud se IntelliTest pokusí [vygenerovat (minimální) sadu vstupů,](input-generation.md) které [plně pokrývají](input-generation.md#dynamic-code-coverage) kód dosažitelný z testu.

PUTs jsou definovány pomocí [pexmethod](attribute-glossary.md#pexmethod) vlastní atribut podobným způsobem jako MSTest (nebo NUnit, xUnit). PUTs jsou metody instance logicky seskupené do tříd označených [třídou PexClass](attribute-glossary.md#pexclass). Následující příklad ukazuje jednoduchý PUT uložené v **MyPexTest** třídy:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

where **ReplaceFirstChar** je metoda, která nahrazuje první znak řetězce:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Z tohoto testu IntelliTest můžete automaticky [generovat vstupy](input-generation.md) pro PUT, který pokrývá mnoho cest spuštění testovaného kódu. Každý vstup, který pokrývá jinou cestu spuštění získá "serializovat" jako testování částí:

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Parametrizované testování částí

Parametrizované testy částí mohou být obecné metody. V takovém případě musí uživatel zadat typy použité k vytvoření instance metody pomocí [pexgenericarguments](attribute-glossary.md#pexgenericarguments).

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Povolení výjimek

IntelliTest poskytuje mnoho atributů ověření, které pomáhají stříděním výjimek do očekávaných výjimek a neočekávaných výjimek.

Očekávané výjimky generovat negativní testovací chvšak s příslušnou poznámkou jako **ExpectedException(typeof(*xxx*))**, zatímco neočekávané výjimky generovat selhání testovacích případů.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Validátory jsou:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): umožňuje určitý typ výjimky odkudkoli
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): umožňuje určitý typ výjimky ze zadaného sestavení.
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): umožňuje určitý typ výjimky ze zadaného typu.
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): umožňuje určitý typ výjimky z testovce typu

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testování vnitřních typů

IntelliTest můžete "test" vnitřní typy, tak dlouho, jak je můžete vidět. Pro IntelliTest zobrazit typy, následující atribut je přidán do produktu nebo testovací projekt průvodci Visual Studio IntelliTest:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Předpoklady a kontrolní výrazy

Uživatelé mohou použít předpoklady a kontrolní výrazy k vyjádření [předpokladů](#precondition) (předpokladů) a [postconditions](#postcondition) (kontrolní výrazy) o jejich testech. Když IntelliTest generuje sadu hodnot parametrů a "zkoumá" kód, může porušit předpoklad testu. Pokud k tomu dojde, nebude generovat test pro tuto cestu, ale bude tiše ignorovat.

Kontrolní výrazy jsou dobře známý koncept v rámci testování pravidelných částí, takže IntelliTest již "chápe" vestavěné **Assert** třídy poskytované každý podporovaný testovací rámec. Většina rozhraní však neposkytují **Assume** třídy. V takovém případě IntelliTest poskytuje [PexAssume](static-helper-classes.md#pexassume) třídy. Pokud nechcete používat existující testovací rámec, IntelliTest má také [PexAssert](static-helper-classes.md#pexassert) třídy.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Zejména předpoklad nenulování lze zakódovat jako vlastní atribut:

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Předběžná podmínka

Předpokladem metody vyjadřuje podmínky, za kterých bude metoda úspěšná.

Předpokladem je obvykle vynuceno kontrolou parametry a stav objektu a vyvolání **ArgumentException** nebo **InvalidOperationException,** pokud je porušena.

V IntelliTest je předběžná podmínka [parametrizovaného testu částí](#parameterized-unit-testing) vyjádřena [pomocí PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Následná podmínka

Koncová podmínka metody vyjadřuje podmínky, které by měly platit během a po provedení metody, za předpokladu, že její předpoklady byly původně platné.

Obvykle je podmínka vynucena voláním **assert** metody.

S IntelliTest je postcondition [parametrizovaného testu částí](#parameterized-unit-testing) vyjádřen [pexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Neúspěšné testy
Kdy se nezdaří vygenerovaný testovací případ?

1. Pokud není ukončena v rámci [nakonfigurované hranice cesty](exploration-bounds.md), je považován za selhání, pokud [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) možnost je nastavena

1. Pokud test vyvolá **PexAssumeFailedException**, je úspěšný. Obvykle se však odfiltruje, pokud není [testemissionfilter](exploration-bounds.md#testemissionfilter) nastaven **na**

1. Pokud test porušuje [tvrzení](#assumptions-and-assertions); například vyvoláním výjimky porušení výrazu rozhraní testování částí, nezdaří se

Pokud žádný z výše uvedených vyrábět rozhodnutí, test uspěje, pokud a pouze v případě, že nevyvolá výjimku. Porušení kontrolního výrazu jsou považovány za výjimky stejným způsobem.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Nastavení a úplné ukončení

Jako součást integrace s testovacími rámci podporuje IntelliTest detekci a spuštění metod nastavení a stržení.

**Příklad**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>Další čtení

* [Test na vazbu kódu](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Jeden test vládnout jim všem](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
