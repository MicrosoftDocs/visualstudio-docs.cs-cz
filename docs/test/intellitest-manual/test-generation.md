---
title: Generování testu | Nástroj Microsoft IntelliTest Developer test Tool
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315171"
---
# <a name="test-generation"></a>Generování testů

V tradičním testování částí se test skládá z několika věcí:

* [Sekvence volání metod](test-generation.md#test-generators)
* Argumenty, které jsou volány metody; argumenty jsou [testovací vstupy](input-generation.md) .
* Ověření zamýšleného chování testované aplikace uvedením sady [kontrolních výrazů](#assumptions-and-assertions)

Následuje příklad struktury testu:

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

IntelliTest může často automaticky určit relevantní hodnoty argumentů pro obecnější [parametrizované testy částí](#parameterized-unit-testing), které poskytují sekvenci volání metod a kontrolních výrazů.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generátory testů

IntelliTest generuje testovací případy tím, že vybere sekvenci metod v testovaném testu, která se má provést, a potom generuje vstupy pro metody při kontrole kontrolních výrazů nad odvozenými daty.

[Parametrizovaný test jednotek](#parameterized-unit-testing) přímo uvádí posloupnost volání metody v těle.

Když IntelliTest potřebuje sestavit objekty, volání konstruktorů a metod továrny se automaticky přidají do sekvence podle potřeby.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametrizované testování částí

*Parametrizované testy jednotek* (vloží) jsou testy, které přijímají parametry. Na rozdíl od tradičních testů jednotek, které jsou obvykle uzavřeny, převezmou všechny sady parametrů. Je to jednoduché? Ano – IntelliTest se pokusí [vygenerovat (minimální) sadu vstupů](input-generation.md) , které [plně pokrývají](input-generation.md#dynamic-code-coverage) kód dosažitelný z testu.

Vložení jsou definována pomocí vlastního atributu [PexMethod](attribute-glossary.md#pexmethod) podobným způsobem jako MSTest (nebo nunit, xUnit). Vloží jsou metody instance logicky seskupené do tříd s příznakem [PexClass](attribute-glossary.md#pexclass). Následující příklad ukazuje jednoduchý objekt PUT uložený ve třídě **MyPexTest** :

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

kde **ReplaceFirstChar** je metoda, která nahrazuje první znak řetězce:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Z tohoto testu IntelliTest může automaticky [Generovat vstupy](input-generation.md) pro vložení, které pokrývá mnoho cest spuštění testovaného kódu. Každý vstup, který pokrývá jinou cestu spuštění, získá "serializovaný" jako test jednotky:

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

Parametrizované testy jednotek můžou být obecné metody. V takovém případě musí uživatel zadat typy používané k vytvoření instance metody pomocí [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

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

IntelliTest poskytuje mnoho ověřovacích atributů, které vám pomůžou roztřídit výjimky na očekávané výjimky a neočekávané výjimky.

Očekávané výjimky generují negativní testovací případy s odpovídající anotací, jako je například **ExpectedException (typeof (*xxx*))**, zatímco neočekávané výjimky generují testovací případy, které selhaly.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Validátory jsou:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): povoluje konkrétní typ výjimky odkudkoli.
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): umožňuje konkrétní typ výjimky ze zadaného sestavení.
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): umožňuje konkrétní typ výjimky ze zadaného typu.
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): umožňuje konkrétní typ výjimky z testovaného typu.

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testování vnitřních typů

IntelliTest může "testovat" interní typy, pokud je uvidí. Pro IntelliTest pro zobrazení typů se do vašeho produktu nebo testovacího projektu pomocí průvodců Visual Studio IntelliTest přidá následující atribut:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Předpoklady a kontrolní výrazy

Uživatelé mohou použít předpoklady a kontrolní výrazy k vyjádření [předběžných podmínek](#precondition) (předpoklady) a [následné podmínky](#postcondition) (kontrolní výrazy) ohledně jejich testů. Když IntelliTest generuje sadu hodnot parametrů a "zkoumá" kód, může dojít k porušení předpokladu testu. Pokud k tomu dojde, nebude se generovat test pro tuto cestu, ale bude tiše ignorovat.

Kontrolní výrazy jsou dobře známý pojem v běžných testovacích architekturách, takže IntelliTest již "rozumí" vestavěnými třídami **Assert** poskytovanými jednotlivými podporovanými testovacími rozhraními. Většina rozhraní však neposkytuje třídu **předpokládat** . V takovém případě IntelliTest poskytuje třídu [PexAssume](static-helper-classes.md#pexassume) . Pokud nechcete použít existující testovací rozhraní, IntelliTest má také třídu [PexAssert](static-helper-classes.md#pexassert) .

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Konkrétně předpokládáme, že předpoklad bez hodnoty null může být kódovaný jako vlastní atribut:

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

Předběžná podmínka metody vyjadřuje podmínky, za kterých bude metoda úspěšná.

Předběžná podmínka je obvykle vyhodnocena kontrolou parametrů a stavu objektu a vyvoláním výjimky **ArgumentException** nebo **InvalidOperationException** , pokud je narušena.

V IntelliTest je předběžnou podmínkou [parametrizovaného testu jednotek](#parameterized-unit-testing) vyjádřeno pomocí [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Následná podmínka

Následná podmínka metody vyjadřuje podmínky, které by měly být zadrženy během a po provedení metody za předpokladu, že jeho předběžné podmínky byly původně platné.

Obvykle je následná podmínka vynutila voláními metod **Assert** .

V IntelliTest je následná podmínka s [parametrizovanou jednotkovým testem](#parameterized-unit-testing) vyjádřen s [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Neúspěšné testy
Kdy dojde k selhání vygenerovaného testovacího případu?

1. Pokud se neukončí v rámci [konfigurované meze cesty](exploration-bounds.md), považuje se za selhání, pokud není nastavená možnost [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) .

1. Pokud test vyvolá **PexAssumeFailedException**, je úspěšný. Je to ale obvykle filtrované, pokud [TestEmissionFilter](exploration-bounds.md#testemissionfilter) není nastavené na **vše** .

1. Pokud test porušuje [kontrolní výraz](#assumptions-and-assertions); například vyvoláním výjimky narušení kontrolního výrazu v rozhraní testování částí se tato chyba nezdařila.

Pokud žádná z výše uvedených nevrátí rozhodnutí, test se úspěšně dokončí pouze v případě, že vyvolá výjimku. Porušení kontrolního výrazu jsou zpracována stejným způsobem jako výjimky.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Nastavení a úplné ukončení

V rámci integrace s testovacími architektura IntelliTest podporuje detekci a spuštění instalačního programu a odtrhnout metody.

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
## <a name="further-reading"></a>Další materiály

* [Testování vazby kódu](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Jeden test pro všechna pravidla](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
