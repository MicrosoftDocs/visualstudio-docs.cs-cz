---
title: Přehled | Nástroj Microsoft IntelliTest Developer test Tool
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 94bd67ecb4646e3b8079d2d1aadda097c655af4c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653176"
---
# <a name="overview-of-microsoft-intellitest"></a>Přehled Microsoft IntelliTest

IntelliTest vám umožňuje najít chyby brzy a snížit náklady na údržbu testů. Pomocí automatizovaného a transparentního testovacího přístupu může IntelliTest vygenerovat kandidátskou sadu testů pro váš kód .NET. Generace sady testů lze dále prověřit *vlastnostmi správnosti* , které zadáte. IntelliTest také automaticky vyvíjí testovací sadu, když se vyvíjí kód v rámci testu.

**Testy charakterizace** IntelliTest umožňuje určit chování kódu v souvislosti se sadou tradičních testů jednotek.
Taková sada testů může být použita jako regresní sada, která vytváří základ pro řešení složitosti spojené s refaktoringem staršího nebo neznámého kódu.

**Generování vstupních testů s asistencí** IntelliTest používá k automatickému vygenerování přesných vstupních hodnot testu a přístup k řešení pro analýzu a omezení kódu. obvykle bez nutnosti zásahu uživatele. U složitých typů objektů automaticky generuje továrny. Vytváření testovacího vstupu můžete nastavit tak, že rozšíříte a nakonfigurujete továrny tak, aby vyhovovaly vašim požadavkům. Vlastnosti správnosti zadané jako kontrolní výrazy v kódu se použijí také automaticky k dalšímu seznámení s vytvářením vstupních testů.

**Integrace IDE** IntelliTest je plně integrovaná do integrovaného vývojového prostředí (IDE) sady Visual Studio. V integrovaném vývojovém prostředí sady Visual Studio se zobrazí všechny informace shromážděné během generování sady testů (například automaticky generované vstupy, výstup z vašeho kódu, vygenerované testovací případy a jejich stav úspěch nebo selhání). Můžete snadno iterovat mezi opravou kódu a IntelliTest, aniž byste opustili integrované vývojové prostředí (IDE) sady Visual Studio.
Testy mohou být uloženy do řešení jako projekt testu jednotek a následně budou automaticky zjišťovány v Průzkumníku testů sady Visual Studio.

**Doplnit stávající postupy testování** Pomocí IntelliTest můžete doplnit všechny stávající postupy testování, které už možná sledujete.

Pokud chcete testovat:

* Algoritmy pro primitivní data nebo pole primitivních dat:
  * zapsat [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing)
* Algoritmy pro složitá data, jako je například kompilátor:
  * IntelliTest nejdřív vygenerujte abstraktní reprezentaci dat a pak ji zapíše do algoritmu.
  * Umožněte IntelliTest instance sestavení pomocí [vlastních objektů pro vytvoření](input-generation.md#objects) a invariantní data a potom tento algoritmus vyvolejte.
* Datové kontejnery:
  * zapsat [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing)
  * Umožněte IntelliTest instance sestavení pomocí [vlastních objektů pro vytvoření](input-generation.md#objects) a invariantní data a potom volejte metodu kontejneru a znovu zkontrolujte invariantní.
  * zapsat [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing) , které volají různé metody implementace, v závislosti na hodnotách parametrů
* Existující základ kódu:
  * Začněte tím, že vygenerujete sadu [parametrizovaných testů jednotek (umístí)](test-generation.md#parameterized-unit-testing) pomocí Průvodce IntelliTest sady Visual Studio.

## <a name="the-hello-world-of-intellitest"></a>Hello World IntelliTest

IntelliTest vyhledá vstupy relevantní testovanému programu, což znamená, že ho můžete použít k vygenerování slavných **Hello World!** řetezce. To předpokládá, že jste vytvořili testovací C# projekt založený na MSTest a Přidali jste odkaz na **Microsoft. Pex. Framework**. Pokud používáte jiné testovací rozhraní, vytvořte knihovnu C# tříd a přečtěte si dokumentaci k testovacímu rozhraní, jak nastavit projekt.

Následující příklad vytvoří dvě omezení pro parametr s názvem **hodnota** tak, aby IntelliTest vygeneroval požadovaný řetězec:

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
2. "\ 0 \ 0 \ 0 \ 0 \ 0"
3. Hello
4. "\ 0 \ 0 \ 0 \ 0 \ 0 \ 0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

Přečtěte si téma [generování testů jednotek pomocí IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) k pochopení, kde jsou vygenerované testy uloženy. Vygenerovaný testovací kód by měl zahrnovat test, jako je například následující kód:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

To je to snadné!

## <a name="limitations"></a>Omezení

Tato část popisuje omezení IntelliTest:

* [Nondeterminism](#nondeterminism)
* [Souběžnost](#concurrency)
* [Nativní kód .NET](#native-code)
* [Platformy](#platform)
* [Jazyk](#language)
* [Symbolický důvod](#symbolic-reasoning)
* [Trasování zásobníku](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Nondeterminism

IntelliTest předpokládá, že analyzovaný program je deterministický. Pokud to tak není, IntelliTest se zacykluje, dokud nedosáhne hranice průzkumu.

IntelliTest považuje program za nedetermisticý, pokud spoléhá na vstupy, které IntelliTest nemůže ovládat.

IntelliTest řídí vstupy poskytované pro [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing) a získané z [PexChoose](static-helper-classes.md#pexchoose).
V tomto smyslu se výsledky volání nespravovaného nebo neinstrumentované kódu považují také za "vstupy" do instrumentované aplikace, ale IntelliTest je nedokáže ovládat. Pokud tok řízení programu závisí na konkrétních hodnotách přicházejících z těchto externích zdrojů, IntelliTest nemůže "řídit" program směrem k dříve nekrytým oblastem.

Kromě toho je program považován za nedetermisticný, pokud se při opětovném spuštění programu změní hodnoty z externích zdrojů. V takových případech IntelliTest ztratí kontrolu nad spuštěním programu a jeho hledání se neefektivně.

V některých případech to není zřejmé, pokud k tomu dojde. Vezměte v úvahu následující příklady:

* Výsledek metody **GetHashCode ()** je poskytován nespravovaným kódem a není předvídatelný.
* Třída **System. Random** používá aktuální systémový čas k zajištění skutečně náhodných hodnot.
* Třída **System. DateTime** poskytuje aktuální čas, který není pod ovládacím prvkem IntelliTest.

### <a name="concurrency"></a>Souběžnost

IntelliTest nezpracovává programy s více vlákny.

### <a name="native-code"></a>Nativní kód

IntelliTest nerozumí nativnímu kódu, jako jsou například instrukce x86 volané prostřednictvím **P/Invoke**. Nevíte, jak přeložit taková volání na omezení, která lze předat [Řešiteli omezení](input-generation.md#constraint-solver).
I pro kód .NET může analyzovat pouze kód IT nástroje. IntelliTest nemůže instrumentovat určité části **knihovny mscorlib**, včetně knihovny reflexe. **Konstruktor DynamicMethod neplatná** nelze instrumentovat.

Navrhovaná alternativní řešení je mít testovací režim, ve kterém se tyto metody nacházejí v typech v dynamickém sestavení. Nicméně i v případě, že některé metody nejsou instrumentované, IntelliTest se pokusí pokrýt co nejvíc instrumentované kódu.

### <a name="platform"></a>Platforma

IntelliTest je podporován pouze v x86, 32-bit. NETframework.

### <a name="language"></a>Jazyk

V zásadě IntelliTest dokáže analyzovat libovolný program .NET, který je napsán v jakémkoli jazyce .NET. V aplikaci Visual Studio však podporuje pouze C#.

### <a name="symbolic-reasoning"></a>Symbolický důvod

IntelliTest používá Řešitel automatického [omezení](input-generation.md#constraint-solver) k určení, které hodnoty jsou relevantní pro test a program v testovaném programu. Nicméně Možnosti řešitele omezení jsou a vždycky budou omezené.

### <a name="incorrect-stack-traces"></a>Nesprávná trasování zásobníku

Vzhledem k tomu, že IntelliTest catch a "rethrows" výjimky v každé instrumentované metodě, čísla řádků v trasování zásobníku nebudou správná. Toto omezení je záměrné návrhem instrukce "Rethrow".

## <a name="further-reading"></a>Další čtení

* [Úvodní Blogový příspěvek](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Generování testů částí pro kód pomocí funkce IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
