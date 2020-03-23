---
title: Úvod do intellitestu
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 113233c985053cfe838f385a36ec59cc211bfcb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591655"
---
# <a name="get-started-with-microsoft-intellitest"></a>Začínáme s Microsoft IntelliTest

* Pokud je to poprvé s IntelliTest:
  * podívejte se na [video kanálu 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * přečtěte si tento [přehled o msdn časopisu](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * přečtěte si naši [dokumentaci](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Zeptejte se na své otázky [na Stack Přetečení](https://stackoverflow.com/questions/tagged/intellitest)
* Přečtěte si zbytek této referenční příručky
* Vytisknout tuto stránku pro rychlou orientaci

## <a name="important-attributes"></a>Důležité atributy

* [PexClass](attribute-glossary.md#pexclass) označuje typ obsahující **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) označuje **PUT**
* [Hodnota PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) označuje nenulový parametr.

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

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) váže testovací projekt k projektu
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) určuje sestavu k nástroji

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a>Důležité statické pomocné třídy

* [PexAssume](static-helper-classes.md#pexassume) vyhodnocuje předpoklady (filtrování vstupů)
* [PexAssert](static-helper-classes.md#pexassert) vyhodnotí kontrolní výrazy
* [PexChoose](static-helper-classes.md#pexchoose) generuje nové volby (další vstupy)
* [PexObserve](static-helper-classes.md#pexobserve) zaznamenává živé hodnoty do generovaných testů.

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

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
