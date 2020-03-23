---
title: Přehled | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: dfa81e7afe313a112e2355ddf5efadb70c555477
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591592"
---
# <a name="overview-of-microsoft-intellitest"></a>Přehled Microsoft IntelliTest

IntelliTest umožňuje najít chyby brzy a snižuje náklady na údržbu testu. Pomocí automatizované a transparentní testování přístup, IntelliTest můžete generovat kandidát sadu testů pro váš kód .NET. Generování testovací sady může být dále vedeno *vlastnostmi správnosti,* které zadáte. IntelliTest bude dokonce vyvíjet testovací sadu automaticky jako testovaný kód se vyvíjí.

**Charakterizační testy** IntelliTest umožňuje určit chování kódu z hlediska sady testů tradičních částí.
Taková testovací sada může být použita jako regresní sada, která je základem pro řešení složitosti spojené s refaktoringem staršího nebo neznámého kódu.

**Generování vstupu testu s průvodcem** IntelliTest používá analýzu otevřeného kódu a přístup k řešení omezení k automatickému generování přesných vstupních hodnot testu; obvykle bez nutnosti zásahu uživatele. U složitých typů objektů automaticky generuje továrny. Generování zkušebních vstupů můžete vést rozšířením a konfigurací továren tak, aby vyhovovaly vašim požadavkům. Správnost vlastnosti zadané jako kontrolní výrazy v kódu budou také automaticky použity k dalšímu spuštění testovacího vstupu.

**Integrace ide** IntelliTest je plně integrován do integrovaného prostředí Visual Studio. Všechny informace shromážděné během generování testovací sady (například automaticky generované vstupy, výstup z kódu, generované testovací případy a jejich stav průchodu nebo selhání) se zobrazí v rámci ide sady Visual Studio. Můžete snadno iterate mezi opravu kódu a opětovné spuštění IntelliTest, aniž by museli opustit IDE sady Visual Studio.
Testy lze uložit do řešení jako projekt testování částí a bude automaticky rozpoznán později Visual Studio Test Explorer.

**Doplnit stávající testovací postupy** Použijte IntelliTest k doplnění všech existujících testovacích postupů, které již můžete dodržovat.

Pokud chcete vyzkoušet:

* Algoritmy nad primitivními daty nebo poli primitivních dat:
  * zapsat [parametrizované jednotkové testy](test-generation.md#parameterized-unit-testing)
* Algoritmy přes komplexní data, jako je například kompilátor:
  * Let IntelliTest nejprve generovat abstraktní reprezentaci dat, a pak je krmit algoritmus
  * Let IntelliTest sestavení instancí pomocí [vlastní vytváření objektů](input-generation.md#objects) a invariants data a potom vyvolat algoritmus
* Datové kontejnery:
  * zapsat [parametrizované jednotkové testy](test-generation.md#parameterized-unit-testing)
  * Let IntelliTest sestavení instancí pomocí [vlastní vytváření objektů](input-generation.md#objects) a invariants data a potom vyvolat metodu kontejneru a znovu zkontrolovat invariants později
  * zapište [parametrizované jednotkové testy,](test-generation.md#parameterized-unit-testing) které volají různé metody implementace v závislosti na hodnotách parametrů
* Existující základ kódu:
  * Pomocí Průvodce IntelliTest sady Visual Studio můžete začít generováním sady [parametrizovaných testů částí (PUT)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Řetězec Hello World u funkce IntelliTest

IntelliTest najde vstupy relevantní pro testovaný program, což znamená, že jej můžete použít ke generování slavného **Hello World!** Řetězec. To předpokládá, že jste vytvořili testovací projekt založený na C# MSTest a přidali odkaz na **Microsoft.Pex.Framework**. Pokud používáte jiný testovací rámec, vytvořte knihovnu tříd jazyka C# a podívejte se na dokumentaci testovacího rámce o tom, jak nastavit projekt.

Následující příklad vytvoří dvě omezení parametru s názvem **value** tak, aby IntelliTest vygeneroval požadovaný řetězec:

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

Po kompilaci a spuštění IntelliTest generuje sadu testů, jako je například následující sada:

1. ""
2. "\0\0\0\0\0"
3. "Dobrý den"
4. "\0\0\0\0\0\0"
5. "Dobrý den\0"
6. "Dobrý den\0\0"
7. "Ahoj\0Svět!"
8. "Ahoj světe!"

> [!NOTE]
> V případě problémů se sestavením zkuste nahradit odkazy microsoft.VisualStudio.TestPlatform.TestFramework a Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions odkazem na Microsoft.VisualStudio.QualityTools.UnitTestFramework.

Přečtěte [si generovat testy částí s IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) pochopit, kde jsou uloženy generované testy. Generovaný testovací kód by měl obsahovat test, například následující kód:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Je to tak snadné!

## <a name="limitations"></a>Omezení

Tato část popisuje omezení IntelliTest:

* [Bez determinismu](#nondeterminism)
* [Souběžnost](#concurrency)
* [Nativní kód .NET](#native-code)
* [Platforma](#platform)
* [Jazyk](#language)
* [Symbolické zdůvodnění](#symbolic-reasoning)
* [Trasování zásobníku](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Bez determinismu

IntelliTest předpokládá, že analyzovaný program je deterministický. Pokud tomu tak není, IntelliTest bude cyklus, dokud nedosáhne průzkumu vázán.

IntelliTest považuje program za nedetermistický, pokud spoléhá na vstupy, které intelliTest nemůže řídit.

IntelliTest řídí vstupy poskytnuté [parametrizovaným testům částí](test-generation.md#parameterized-unit-testing) a získané z [PexChoose](static-helper-classes.md#pexchoose).
V tomto smyslu jsou výsledky volání nespravovaného nebo neinstrumentovaného kódu také považovány za "vstupy" do instrumentovaného programu, ale IntelliTest je nemůže řídit. Pokud tok řízení programu závisí na konkrétních hodnotách pocházejících z těchto externích zdrojů, intelliTest nemůže "řídit" program směrem k dříve nekrytým oblastem.

Kromě toho je program považován za nedetermistický, pokud se hodnoty z externích zdrojů změní při opětovném spuštění programu. V takových případech IntelliTest ztratí kontrolu nad provádění programu a jeho hledání se stane neefektivní.

Někdy to není zřejmé, když se to stane. Zvažte následující příklady:

* Výsledek **GetHashCode()** metoda je poskytována nespravovaný kód a není předvídatelné.
* Třída **System.Random** používá aktuální systémový čas k dodání skutečně náhodných hodnot.
* Třída **System.DateTime** poskytuje aktuální čas, který není pod kontrolou IntelliTest.

### <a name="concurrency"></a>Souběžnost

IntelliTest nezpracovává vícevláknové programy.

### <a name="native-code"></a>Nativní kód

IntelliTest nerozumí nativnímu kódu, například x86 instrukce volané prostřednictvím **P/Invoke**. Neví, jak převést tato volání do omezení, která mohou být předána [řešiči omezení](input-generation.md#constraint-solver).
I pro kód .NET může analyzovat pouze kód, který instrumentuje. IntelliTest nelze instrumentace určité části **mscorlib**, včetně reflexe knihovny. **DynamicMethod** nelze instrumentovat.

Navrhované řešení je mít testovací režim, kde jsou tyto metody umístěny v typech v dynamickém sestavení. Však i v případě, že některé metody jsou neinstrumentované, IntelliTest se pokusí pokrýt co nejvíce instrumentovaný kód, jak je to možné.

### <a name="platform"></a>Platforma

IntelliTest je podporován pouze na X86, 32-bit . Netframework.

### <a name="language"></a>Jazyk

V zásadě může IntelliTest analyzovat libovolné programy .NET napsané v libovolném jazyce .NET. Však v sadě Visual Studio podporuje pouze C#.

### <a name="symbolic-reasoning"></a>Symbolické zdůvodnění

IntelliTest používá automatický [řešič omezení](input-generation.md#constraint-solver) k určení, které hodnoty jsou relevantní pro test a testovce testovce. Schopnosti řešiče omezení jsou a vždy budou omezené.

### <a name="incorrect-stack-traces"></a>Nesprávná trasování zásobníku

Vzhledem k tomu, že IntelliTest zachytí a "znovu vyvolá" výjimky v každé instrumentované metody, čísla řádků v trasování zásobníku nebude správné. Toto je omezení záměrné instrukce "rethrow".

## <a name="further-reading"></a>Další čtení

* [Úvodní blogový příspěvek](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Generování testů částí pro kód pomocí funkce IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
