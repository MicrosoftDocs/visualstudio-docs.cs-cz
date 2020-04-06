---
title: Začínáme s Roslyn Analyzátory | Dokumenty společnosti Microsoft
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711263"
---
# <a name="get-started-with-roslyn-analyzers"></a>Začínáme s analyzátory Roslyn

Pomocí živých analyzátorů kódu založených na projektu v sadě Visual Studio mohou autoři rozhraní API doručovat analýzu kódu specifickou pro doménu jako součást svých balíčků NuGet. Vzhledem k tomu, že tyto analyzátory jsou napájeny platformou kompilátoru .NET (s kódovým názvem "Roslyn"), mohou vytvářet upozornění ve vašem kódu při psaní ještě předtím, než dokončíte řádek (žádné další čekání na sestavení kódu ke zjištění problémů). Analyzátory můžete také povrch automatické opravy kódu prostřednictvím výzvy žárovky Visual Studio, aby vám umožní vyčistit kód okamžitě.

## <a name="get-started"></a>Začínáme

[Roslyn analyzátory přehled](../code-quality/roslyn-analyzers-overview.md)

[Kurz: Napište svůj první analyzátor a opravu kódu](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Přidání kódu opravy Návod: Poskytnout uživatelům opravy pro problémy analyzátoru](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Skutečný svět Roslyn analyzátor,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) který můžete také sledovat jako [mluvit](https://channel9.msdn.com/events/Build/2015/3-725)

[Několik příkladů na GitHubu, seskupených do tří druhů analyzátorů](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Viz také

- [Odkaz na verzi balíčku kompilátoru rozhraní .NET](roslyn-version-support.md)
- [Další dokumenty na webu GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [FxCop pravidla implementována s analyzátory Roslyn](../code-quality/fxcop-rule-port-status.md)
