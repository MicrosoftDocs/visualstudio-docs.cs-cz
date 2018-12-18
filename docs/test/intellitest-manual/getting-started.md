---
title: Úvod k Intellitestu
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3e33bab90c32ca1b7cd92714218e5694daa22aed
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000736"
---
# <a name="get-started-with-microsoft-intellitest"></a>Začínáme s Microsoft IntelliTest

* Pokud to je poprvé s Intellitestem:
  * Podívejte [videa Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * Přečtěte si tento [přehled na webu MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * Přečtěte si naše [dokumentace](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Pokládání otázek na [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest)
* Čtení zbývajících částí této referenční příručce
* Vytiskněte si tuto stránku Stručná referenční příručka

## <a name="important-attributes"></a>Důležité atributy

* [PexClass](attribute-glossary.md#pexclass) označuje typ obsahující **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) značky **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) označí nenulový parametr

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

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) váže testovací projekt na projekt
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) určuje sestavení, k Sestrojení

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> Třídy statických pomocných rutin důležité

* [PexAssume](static-helper-classes.md#pexassume) vyhodnotí předpoklady (vstupní filtrování)
* [PexAssert](static-helper-classes.md#pexassert) vyhodnotí výrazy
* [PexChoose](static-helper-classes.md#pexchoose) generuje nové možnosti (další vstupy)
* [PexObserve](static-helper-classes.md#pexobserve) zaznamená živé hodnoty do vygenerované testy

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

## <a name="got-feedback"></a>Máte nějakou zpětnou vazbu?

Publikovat své nápady a funkce na požadavky [komunity vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
