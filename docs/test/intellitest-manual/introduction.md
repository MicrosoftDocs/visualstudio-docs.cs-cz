---
title: Přehled | Nástroj pro testování Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c2a8e6df93d3af64bd114e0e9994aadce58e7f8d
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296018"
---
# <a name="overview-of-microsoft-intellitest"></a>Přehled Microsoft IntelliTest

IntelliTest umožňuje najít chyby již v rané fázi a snižuje náklady na údržbu testů. Pomocí automatizovaných a transparentní přístup testování, Intellitestu můžete vygenerovat Release candidate sady testování pro kód .NET. Generování testu suite můžete dále řídí *vlastností správnosti* zadáte. IntelliTest se i vyvíjet sady testů automaticky s vyvíjí testovaného kódu.

**Testy charakteristiku** IntelliTest umožňuje určit chování kódu z hlediska sadu tradiční jednotkové testy.
Testovací sada může sloužit jako sada regrese, které tvoří základ pro zvládnutí složitost spojenou s refaktoring starší verze nebo neznámého kódu.

**Praktická testovací vstup generování** IntelliTest používá analýzy kódu otevřete a omezení řešení přístup k automatickému generování přesné testovací vstupní hodnoty; obvykle bez nutnosti zásahu uživatele. Pro komplexní typy objektů se automaticky generuje objekty pro vytváření. Vstupní generování testu můžete Průvodce rozšířením a konfigurace továrny tak, aby vyhovoval vašim požadavkům. Byly zadány jako kontrolní výrazy v kódu se také použít automaticky k další vygenerování testovacích vstupní vlastnosti správnosti.

**Integrace integrovaného vývojového prostředí** IntelliTest je plně integrován do integrovaného vývojového prostředí sady Visual Studio. Všechny informace shromážděné během generování sady testů (např. automaticky generované vstupů, výstup z kódu, vygenerované testovací případy a jejich průchodu nebo neúspěch stav) se zobrazí v rámci rozhraní IDE sady Visual Studio. Můžete snadno iterovat mezi opravu kódu a znovu spustit inteligentní testování, aniž byste museli opustit integrované vývojové prostředí sady Visual Studio.
Testy mohou být uloženy do řešení jako projekt testování částí a bude možné automaticky detekovat později pomocí Visual Studio Test Explorer.

**Doplňují existující testování postupů** použití IntelliTest doplnit existující testování postupy, že již mohou následovat.

Pokud chcete testovat:

* Algoritmy přes primitivní datové nebo primitivní datové pole:
  * zápis [parametrizované testy částí](test-generation.md#parameterized-unit-testing)
* Algoritmy složitých dat, jako je například kompilátor:
  * umožní IntelliTest nejprve generovat abstraktní znázornění dat a informační kanál algoritmus
  * umožnit vytváření instancí pomocí funkce IntelliTest [vytváření vlastních objektů](input-generation.md#objects) a výstupních dat podmínek a pak vyvolejte algoritmus
* Kontejnery dat:
  * zápis [parametrizované testy částí](test-generation.md#parameterized-unit-testing)
  * umožnit vytváření instancí pomocí funkce IntelliTest [vytváření vlastních objektů](input-generation.md#objects) a výstupních dat podmínek a vyvolat metodu kontejneru a potom spusťte opětovnou kontrolu výstupních podmínek
  * zápis [parametrizované testy částí](test-generation.md#parameterized-unit-testing) , které volají různé metody provedení, v závislosti na hodnoty parametrů
* Existující kódové základně:
  * pomocí Průvodce Intellitestu sady Visual Studio můžete začít tím, že generování sadu [parametrizované testy částí (vloží)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Hello World intellitestu

IntelliTest najde vstupy relevantní pro otestované program, to znamená, slouží ke generování známý **Hello World!** řetězec. Předpokladem je, že jste vytvořili C# založené na MSTest testovací projekt a přidat odkaz na **Microsoft.Pex.Framework**. Pokud používáte jiný testovací rozhraní, vytvořte C# knihovna tříd a najdete v dokumentaci rozhraní framework test v nastavení projektu.

Následující příklad vytvoří dvě omezení na parametr s názvem **hodnotu** tak, aby IntelliTest vygeneruje požadovaný řetězec:

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

Jakmile zkompilovat a spustit, Intellitestu generuje sadu testů, jako je následující:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

Čtení [generování testů jednotek s Intellitestem](../../test/generate-unit-tests-for-your-code-with-intellitest.md) pochopit, kde jsou uloženy vygenerované testy. Kód generovaný test by měl obsahovat testu, jako je například následující kód:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Je to snadné!

## <a name="limitations"></a>Omezení

Tato část popisuje omezení IntelliTest:

* [Nondeterminism](#nondeterminism)
* [Souběžnost](#concurrency)
* [Nativní kód .NET](#native-code)
* [Platforma](#platform)
* [Jazyk](#language)
* [Symbolického uvažování](#symbolic-reasoning)
* [Trasování zásobníku](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Nondeterminism

IntelliTest předpokládá, že je analyzované program deterministický. Pokud není, IntelliTest se cyklus, dokud nedosáhne vysvětlení vázán.

IntelliTest bere v úvahu program, který se bez determistic, pokud závisí na vstupy, které nemůžeme mít pod kontrolou IntelliTest.

IntelliTest ovládací prvky na zadané vstupy [parametrizované testy částí](test-generation.md#parameterized-unit-testing) a které byly získány z [PexChoose](static-helper-classes.md#pexchoose).
V tomto smyslu výsledky volání neinstrumentované nebo nespravovaného kódu se také považují za "vstupy" instrumentované aplikace, ale IntelliTest je řídit. Pokud tok řízení programu závisí na konkrétní hodnoty pocházejí z těchto externích zdrojů, Intellitestu nelze "řídit" program směrem k dříve nepokrytý oblasti.

Kromě toho program se považuje za jiných determistic Pokud změny hodnot z externích zdrojů, když znovu spustit program. V takových případech IntelliTest ztratí kontrolu nad provádění programu a hledání se stane neefektivní.

Někdy není zřejmé Pokud k tomu dojde.
Vezměte v úvahu následující příklady:

* Výsledkem **GetHashCode()** metoda je poskytována nespravovaného kódu a není předvídatelný.
* **System.Random** třída používá aktuální systémový čas k zajištění skutečně náhodné hodnoty.
* **System.DateTime** třída poskytuje aktuální čas, který není pod kontrolou IntelliTest.

### <a name="concurrency"></a>Souběžnost

IntelliTest nezpracovává s více vlákny.

### <a name="native-code"></a>Nativní kód

IntelliTest nerozumí nativního kódu, jako je například x86 pokyny zavolaném prostřednictvím **P/Invoke**. Nemůže určit způsob převodu těchto volání do omezení, která mohou být předány [Řešitel omezení](input-generation.md#constraint-solver).
I pro kód .NET se může analyzovat jenom kód, který jej instrumentovat. IntelliTest se nedá instrumentovat některých částí **mscorlib**, včetně knihovnu reflexe. **Konstruktor DynamicMethod** nemůže být instrumentované.

Navrhovaná alternativní řešení je, aby zkušební režim, kde tyto metody jsou umístěny v typech v dynamickém sestavení. Ale i v případě, že jsou některé metody neinstrumentované, IntelliTest se pokouší zakrýt největší instrumentované kódu, jako je to možné.

### <a name="platform"></a>Platforma

IntelliTest se podporuje jenom na X86, 32 bitů. NETframework.

### <a name="language"></a>Jazyk

V zásadě můžete analyzovat IntelliTest libovolného programy .NET vytvořené v kterémkoli jazyce platformy .NET. Ale v sadě Visual Studio podporuje pouze C#.

### <a name="symbolic-reasoning"></a>Symbolického uvažování

IntelliTest používá automatické [Řešitel omezení](input-generation.md#constraint-solver) k určení hodnot, které jsou relevantní pro testovací a testovaném programu. Nicméně jsou možnosti řešení omezení a stále bude, omezené.

### <a name="incorrect-stack-traces"></a>Trasování zásobníku nesprávný

Protože IntelliTest zachytí a "znovu vyvolá" výjimky v každé metodě instrumentované čísla řádků v trasování zásobníku nebudou správná. Jedná se o omezení podle návrhu "přegenerování" instrukce.

## <a name="further-reading"></a>Další čtení

* [Úvodní blogový příspěvek](https://blogs.msdn.microsoft.com/devops/2014/11/19/introducing-smart-unit-tests/).
* [Generování testů částí pro kód pomocí funkce IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
