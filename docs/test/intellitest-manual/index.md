---
title: Přehled | Testovací nástroj pro vývojáře Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5eb619269dfd8922919999249b4ced0b9b98ebb7
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256202"
---
# <a name="overview-of-microsoft-intellitest"></a>Přehled nástroje Microsoft IntelliTest

IntelliTest vám umožňuje brzy najít chyby a snížit náklady na údržbu testů. Pomocí automatizovaného a transparentního testovacího přístupu může IntelliTest vygenerovat kandidátskou sadu testů pro váš kód .NET. Generování sady testů se dá dále řídit pomocí *vlastností správnosti*, které zadáte. IntelliTest také umí automaticky vyvíjet sadu testů, jak se vyvíjí kód v rámci testu.

**Charakterizační testy**: IntelliTest umožňuje určit chování kódu v rámci sady tradičních testů jednotek.
Taková sada testů může být použita jako regresní sada, která tvoří základ pro řešení složitosti spojené s refaktoringem staršího nebo neznámého kódu.

**Generování vstupu pro testy s asistencí**: IntelliTest používá otevřený přístup k analýze kódu a řešení omezení, aby mohl automaticky generovat přesné vstupní hodnoty testů – a to obvykle bez nutnosti zásahu uživatele. U složitých objektových typů automaticky generuje objekty pro vytváření (factory). Vytváření vstupu pro testy můžete vést tak, že rozšíříte a nakonfigurujete objekty factory tak, aby vyhovovaly vašim požadavkům. Vlastnosti správnosti zadané jako kontrolní výrazy v kódu se také automaticky použijí k dalšímu vedení vytváření vstupu pro testy.

**Integrace do IDE**: IntelliTest je plně integrovaný do integrovaného vývojového prostředí (IDE) sady Visual Studio. V integrovaném vývojovém prostředí sady Visual Studio se zobrazí všechny informace shromážděné během generování sady testů (například automaticky generované vstupy, výstup z vašeho kódu, vygenerované testovací případy a jejich stav – úspěch nebo neúspěch). Můžete snadno iterovat mezi opravou kódu a spouštěním IntelliTestu, aniž byste opustili integrované vývojové prostředí sady Visual Studio.
Testy se dají uložit do řešení jako Projekt testů jednotek, kde je pak automaticky zjistí Průzkumník testů sady Visual Studio.

**Doplňování stávajících postupů testování**: IntelliTest můžete používat k doplňování stávajících postupů testování, podle kterých už možná postupujete.

Pokud chcete testovat:

* Algoritmy v primitivních datech, nebo pole primitivních dat:
  * zapište [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing).
* Algoritmy ve složitých datech, jako je například kompilátor:
  * nechte IntelliTest nejdřív vygenerovat abstraktní reprezentaci dat a pak ji zapište do algoritmu.
  * nechte IntelliTest sestavit instance pomocí [vytvoření vlastního objektu](input-generation.md#objects) a invariantů dat a potom tento algoritmus vyvolejte.
* Datové kontejnery:
  * zapište [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing).
  * nechte IntelliTest sestavit instance pomocí [vytvoření vlastního objektu](input-generation.md#objects) a invariantů dat a potom vyvolejte metodu kontejneru a následně znovu zkontrolujte invarianty.
  * zapište [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing), které volají různé metody implementace v závislosti na hodnotách parametrů.
* Existující základ kódu:
  * začněte tím, že pomocí Průvodce IntelliTest sady Visual Studio vygenerujete sadu [parametrizovaných testů jednotek (PUT)](test-generation.md#parameterized-unit-testing).

## <a name="the-hello-world-of-intellitest"></a>Řetězec Hello World u funkce IntelliTest

IntelliTest hledá vstupy relevantní k testovanému programu, což znamená, že ho můžete použít k vygenerování známého řetězce **Hello World!** . Předpokladem je, že jste vytvořili projekt testů v C# založený na MSTestu a přidali jste odkaz na **Microsoft.Pex.Framework**. Pokud používáte jinou testovací architekturu, vytvořte knihovnu tříd C# a podívejte se do dokumentace k testovací architektuře, jak nastavit projekt.

Následující příklad vytvoří dvě omezení pro parametr s názvem **value** tak, aby IntelliTest vygeneroval požadovaný řetězec:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Po kompilaci a provedení IntelliTest vygeneruje sadu testů, jako je následující sada:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

> [!NOTE]
> V případě problémů se sestavením zkuste nahradit odkazy Microsoft.VisualStudio.TestPlatform.TestFramework a Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions odkazem na Microsoft.VisualStudio.QualityTools.UnitTestFramework.

Přečtěte si [Vygenerování testů jednotek pomocí IntelliTestu](../../test/generate-unit-tests-for-your-code-with-intellitest.md), ať víte, kam se vygenerované testy ukládají. Vygenerovaný testovací kód by měl zahrnovat test, jako je například následující kód:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Tak je to snadné!

Další prostředky:
  * Podívejte se na [video Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest).
  * Přečtěte si tento [přehled na webu MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx).

## <a name="important-attributes"></a>Důležité atributy

* [PexClass](attribute-glossary.md#pexclass) označuje typ obsahující **PUT** (parametrizovaný test jednotek).
* [PexMethod](attribute-glossary.md#pexmethod) označuje **PUT**.
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) označuje parametr, který není null.

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) váže projekt testů k projektu.
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) určuje sestavení pro instrumentaci.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a> Důležité třídy statických pomocných rutin

* [PexAssume](static-helper-classes.md#pexassume) vyhodnocuje předpoklady (filtrování vstupu).
* [PexAssert](static-helper-classes.md#pexassert) vyhodnocuje kontrolní výrazy.
* [PexChoose](static-helper-classes.md#pexchoose) generuje nové volby (další vstupy).
* [PexObserve](static-helper-classes.md#pexobserve) zaznamenává živé hodnoty do vygenerovaných testů.

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="limitations"></a>Omezení

Tato část popisuje omezení IntelliTestu:

* [Bez determinismu](#nondeterminism)
* [Souběžnost](#concurrency)
* [Nativní kód .NET](#native-code)
* [Platforma](#platform)
* [Jazyk](#language)
* [Symbolické zdůvodnění](#symbolic-reasoning)
* [Trasování zásobníků](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Bez determinismu

IntelliTest předpokládá, že analyzovaný program je deterministický. Pokud to tak není, IntelliTest se zacyklí, dokud nedosáhne meze průzkumu.

IntelliTest považuje program za nedetermisticý, pokud spoléhá na vstupy, které IntelliTest nemůže ovládat.

IntelliTest řídí vstupy poskytované pro [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing) a získané z [PexChoose](static-helper-classes.md#pexchoose).
V tomto smyslu se výsledky volání nespravovaného nebo neinstrumentovaného kódu považují také za vstupy do instrumentovaného programu, ale IntelliTest je nemůže ovládat. Pokud tok řízení programu závisí na konkrétních hodnotách přicházejících z těchto externích zdrojů, IntelliTest nemůže „vést“ program směrem k dříve nepokrytým oblastem.

Kromě toho je program považován za nedetermisticný, pokud se při opětovném spuštění programu změní hodnoty z externích zdrojů. V takových případech IntelliTest ztratí kontrolu nad spuštěním programu a jeho hledání se stává neefektivní.

V některých případech to není zřejmé, když k tomu dojde. Představte si následující příklady:

* Výsledek metody **GetHashCode ()** je poskytován nespravovaným kódem a není předvídatelný.
* Třída **System.Random** používá aktuální systémový čas k zajištění skutečně náhodných hodnot.
* Třída **System.DateTime** poskytuje aktuální čas, který není pod kontrolou IntelliTestu.

### <a name="concurrency"></a>Souběžnost

IntelliTest nezpracovává programy s více vlákny.

### <a name="native-code"></a>Nativní kód

IntelliTest nerozumí nativnímu kódu, jako jsou například instrukce x86 volané prostřednictvím **P/Invoke**. Neví, jak přeložit taková volání na omezení, která je možné předat [řešiteli omezení](input-generation.md#constraint-solver).
I pro kód .NET může analyzovat jenom kód, který instrumentuje. IntelliTest nemůže instrumentovat určité části **mscorlib**, včetně knihovny reflexe. **DynamicMethod** nejde instrumentovat.

Navrhované alternativní řešení je mít testovací režim, ve kterém se tyto metody nacházejí v typech v dynamickém sestavení. Nicméně i v případě, že některé metody nejsou instrumentované, IntelliTest se pokusí pokrýt co možná nejvíc instrumentovaného kódu.

### <a name="platform"></a>Platforma

IntelliTest je podporovaný jenom v 32bitové architektuře .NETframework X86.

### <a name="language"></a>Jazyk

IntelliTest v zásadě dokáže analyzovat libovolné programy .NET napsané v jakémkoliv jazyce .NET. V sadě Visual Studio však podporuje jenom C#.

### <a name="symbolic-reasoning"></a>Symbolické zdůvodnění

IntelliTest používá k určení, které hodnoty jsou relevantní pro test a testovaný program, automatického [řešitele omezení](input-generation.md#constraint-solver). Nicméně možnosti řešitele omezení jsou a vždycky budou omezené.

### <a name="incorrect-stack-traces"></a>Nesprávná trasování zásobníků

Vzhledem k tomu, že IntelliTest zachytává a „znovu vypouští“ výjimky v každé instrumentované metodě, čísla řádků v trasování zásobníků nebudou správná. Toto omezení je součástí instrukce „opětovného vypouštění“ (rethrow).

## <a name="further-reading"></a>Další čtení

* [Úvodní blogový příspěvek](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/)
* [Generování testů jednotek pro kód pomocí funkce IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
