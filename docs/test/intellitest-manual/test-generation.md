---
title: Generování testů | Nástroj pro testování Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 20bacca2343cb2689ed52096c1a9b0d9c3d74703
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295862"
---
# <a name="test-generation"></a>Generování testů

V tradičních testování částí test se skládá z několik věcí:

* A [posloupnost volání metod](test-generation.md#test-generators)
* Argumenty, se kterými volání těchto metod; argumenty jsou [testovací vstupy](input-generation.md)
* Ověření zamýšlené chování testované aplikace uvedením sadu [kontrolní výrazy](#assumptions-and-assertions)

Toto je test struktury příklad:

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

IntelliTest často automaticky rozpozná hodnoty argumentů relevantní pro obecnější [parametrizovaných testů jednotek](#parameterized-unit-testing), které poskytují posloupnost volání metody a kontrolní výrazy.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generátory testu

IntelliTest generuje testovací případy výběrem posloupnost metody provádění v rámci spuštění testu, a potom generování vstupů pro metody při kontrole nad daty odvozené kontrolní výrazy.

A [parametrizovaný test části](#parameterized-unit-testing) přímo státy pořadí metody volá v těle.

Když IntelliTest potřebuje k vytvoření objektů, volání konstruktorů a metod objekt pro vytváření se přidají automaticky pořadí podle potřeby.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametrizované testování částí

*Parametrizované testy částí* (vloží) jsou testy, které přijímají parametry. Na rozdíl od tradičních jednotkové testy, které jsou obvykle zavřené metody, vloží trvat libovolnou sadu parametrů. Je to jednoduché? Ano – odtud IntelliTest se pokusí [generovat (minimální) sadu vstupů](input-generation.md) , který [plně zahrnují](input-generation.md#dynamic-code-coverage) dosažitelný z testovacího kódu.

Vloží jsou definovány pomocí [PexMethod](attribute-glossary.md#pexmethod) vlastního atributu podobným způsobem MSTest (nebo NUnit, xUnit). Vloží jsou logicky seskupeny do třídy označené metody instance [PexClass](attribute-glossary.md#pexclass). Následující příklad ukazuje jednoduchý PUT uložené v **MyPexTest** třídy:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

kde **ReplaceFirstChar** je metoda, která nahradí první znak řetězce:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Tento test posuzujeme IntelliTest může automaticky [generovat vstupy](input-generation.md) pro PUT, která zahrnuje mnoho cesty spuštění testovaného kódu. Každá vstupní, že jako testování částí, která se vztahuje různých pracovních cestu získá "serializovat":

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
## <a name="generic-parameterized-unit-testing"></a>Obecné parametry testování částí

Parametrizované testy částí, může být obecné metody. V takovém případě musí uživatel zadat typy použité k vytvoření instance metodu pomocí [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

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

IntelliTest poskytuje mnoho atributů ověření třídění výjimky na očekávané výjimky a neočekávané výjimky.

Očekávané výjimky generovat negativní testovací případy s odpovídající poznámkou jako **ExpectedException (typeof (*xxx*))**, generovat neočekávané výjimky selhání testovací případy.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Validátory jsou:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): umožňuje typ konkrétní výjimky z libovolného místa
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): umožňuje typ konkrétní výjimky ze zadaného sestavení
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): umožňuje typ konkrétní výjimky ze zadaného typu
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): umožňuje typ konkrétní výjimky z typu v rámci testu

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testování vnitřní typy

IntelliTest můžete "test" vnitřní typy, tak dlouho, dokud jej můžete zobrazit. Pro Intellitestu a zjistit typy následující atribut přidali do svého produktu nebo testovacího projektu pomocí průvodců Visual Studio IntelliTest:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Předpoklady a kontrolní výrazy

Uživatelé můžou pomocí předpoklady a kontrolní výrazy express [předběžné podmínky](#precondition) (předpoklady) a [vstupních](#postcondition) (kontrolní výrazy) o jejich testy. Když IntelliTest generuje sadu hodnot parametrů a "zkoumá" kód, může porušovat předpokládá testu. Pokud k tomu dojde, nebude generovat testu pro tuto cestu, ale bude tiše ignorovat.

Kontrolní výrazy jsou dobře známé koncept v rozhraní pro testování částí pravidelně, tak IntelliTest již "rozumí" integrovaného **Assert** tříd poskytovaných v jednotlivých podporovaných testovacího rozhraní. Však neposkytují většina architektur **předpokládat** třídy. V takovém případě IntelliTest poskytuje [PexAssume](static-helper-classes.md#pexassume) třídy. Pokud nechcete použít existující testovací rozhraní, Intellitestu má také [PexAssert](static-helper-classes.md#pexassert) třídy.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Zejména předpokladů hodnotu Null, může být zakódován jako vlastní atribut:

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Předběžné podmínky

Předběžná podmínka metody vyjadřuje podmínky, za kterých bude úspěšné metodu.

Obvykle je předpoklad vynuceny kontroly parametrů a stav objektu a vyvolání **ArgumentException** nebo **InvalidOperationException** Pokud je porušena.

V IntelliTest předpokladem [parametrizovaný test části](#parameterized-unit-testing) je vyjádřené pomocí [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Neplatná následná

Neplatná následná metody vyjadřuje podmínky, které by měly mít během a po spuštění metody, za předpokladu, že jeho předpoklady byly původně platný.

Obvykle se vynucuje neplatná následná volání **Assert** metody.

Pomocí funkce IntelliTest neplatná následná z [parametrizovaný test části](#parameterized-unit-testing) je vyjádřené pomocí [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Neúspěšné testy
Když vygenerované testovací případ selhání?

1. Jestliže neskončí v rámci [nakonfigurovaná cesta hranice](exploration-bounds.md), se považují za selhání, pokud [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) nastavená možnost

1. Pokud vyvolá testu **PexAssumeFailedException**, neproběhne úspěšně. Ale to je obvykle odfiltrována Pokud [TestEmissionFilter](exploration-bounds.md#testemissionfilter) je nastavena na **všechny**

1. Pokud test je v rozporu [kontrolní výraz](#assumptions-and-assertions); například vyvoláním výjimku kontrolního výrazu porušení jednotkových testů se nezdaří

Pokud žádná z výše uvedené vytvoří rozhodnutí, test bude úspěšné pouze v případě nevyvolá výjimku. Kontrolní výraz porušení zachází stejně jako výjimky.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Nastavení a dovolí

IntelliTest podporuje zjišťování a spuštění v rámci integrace s rozhraní pro testování, nastavení a dovolí metody.

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

* [Testování vazby kódu](https://blogs.msdn.microsoft.com/devops/2015/04/18/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Jeden test pro vládne všem.](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Máte nějakou zpětnou vazbu?

Publikovat své nápady a funkce na požadavky [komunity vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).