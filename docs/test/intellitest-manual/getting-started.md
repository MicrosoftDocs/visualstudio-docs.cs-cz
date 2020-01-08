---
title: Úvod do IntelliTest
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591655"
---
# <a name="get-started-with-microsoft-intellitest"></a>Začínáme s Microsoft IntelliTest

* Pokud používáte IntelliTest poprvé:
  * Podívejte se na [video o kanálu 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest) .
  * Přečtěte si tento [Přehled na webu MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx) .
  * Přečtěte si naši [dokumentaci](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Položte své dotazy na [Stack Overflow](https://stackoverflow.com/questions/tagged/intellitest)
* Přečtěte si zbytek tohoto referenčního návodu.
* Tisk této stránky pro rychlé odkazy

## <a name="important-attributes"></a>Důležité atributy

* [PexClass](attribute-glossary.md#pexclass) označuje typ obsahující **Put** .
* [PexMethod](attribute-glossary.md#pexmethod) označuje **Put**
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
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) určuje sestavení pro instrumentaci

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a>Důležité statické pomocné třídy

* [PexAssume](static-helper-classes.md#pexassume) vyhodnocuje předpoklady (filtrování vstupu).
* [PexAssert](static-helper-classes.md#pexassert) vyhodnocuje kontrolní výrazy
* [PexChoose](static-helper-classes.md#pexchoose) vygeneruje nové volby (další vstupy).
* [PexObserve](static-helper-classes.md#pexobserve) zaznamená živé hodnoty do vygenerovaných testů

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

Publikujte své nápady a žádosti o funkce na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
