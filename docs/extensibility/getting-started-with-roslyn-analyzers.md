---
title: Začínáme s analyzátory Roslyn | Microsoft Docs
description: Pomocí těchto zdrojů můžete začít s analyzátory Roslyn v aplikaci Visual Studio; Obsahuje kurz a několik příkladů.
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4579f148d2e27961fe1c579ffe3583e0e6be806c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057595"
---
# <a name="get-started-with-roslyn-analyzers"></a>Začínáme s analyzátory Roslyn

S živými analyzátory kódu založenými na projektech v aplikaci Visual Studio můžou autoři rozhraní API dodávat analýzu kódu specifickou pro doménu jako součást jejich balíčků NuGet. Vzhledem k tomu, že tyto analyzátory využívají .NET Compiler Platform (kód s názvem "Roslyn"), mohou ve vašem kódu při psaní vydávat upozornění, i když jste dokončili řádek (nečekáte na sestavení kódu pro zjišťování problémů). Analyzátory mohou také automaticky opravovat opravy kódu prostřednictvím výzvy k vyčistění kódu přímo v programu Visual Studio Light žárovky.

## <a name="get-started"></a>Začínáme

[Přehled analyzátorů Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Kurz: vytvoření prvního analyzátoru a opravy kódu](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Postup přidání oprav kódu Návod: poskytnutí oprav pro problémy s analyzátorem pro uživatele](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , který můžete také sledovat jako [rozhovor](https://channel9.msdn.com/events/Build/2015/3-725)

[Několik příkladů na GitHubu, seskupené do tří druhů analyzátorů](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Viz také

- [Reference k verzi balíčku platformy .NET Compiler](roslyn-version-support.md)
- [Další dokumentace na webu GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Pravidla FxCop implementovaná pomocí analyzátorů Roslyn](../code-quality/fxcop-rule-port-status.md)
