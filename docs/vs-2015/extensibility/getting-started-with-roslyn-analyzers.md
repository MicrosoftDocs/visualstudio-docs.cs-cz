---
title: Začínáme s Roslyn Analyzátory | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444962"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Začínáme s analyzátory Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí živých analyzátorů kódu založených na projektu v sadě Visual Studio mohou autoři rozhraní API doručovat analýzu kódu specifickou pro doménu jako součást svých balíčků NuGet.  Vzhledem k tomu, že tyto analyzátory jsou napájeny platformou kompilátoru .NET (s kódovým názvem "Roslyn"), mohou vytvářet upozornění ve vašem kódu při psaní ještě předtím, než dokončíte řádek (žádné další čekání na sestavení kódu ke zjištění problémů).  Analyzátory mohou také povrch automatické opravy kódu prostřednictvím výzvy žárovky Visual Studio, aby vám umožní vyčistit kód okamžitě

## <a name="getting-started"></a>začínáme
[Úvod a návod analyzátory živého kódu Roslyn](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Návod k přidání oprav kódu: Poskytněte uživatelům opravy problémů s analyzátorem](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Úvod a návod na Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) že můžete také sledovat jako [mluvit](https://channel9.msdn.com/events/Build/2015/3-725)

[Několik příkladů na GitHubu, seskupených do tří druhů analyzátorů](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Úvod a prohlídka několika analyzátorů Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Další prostředky
[Další dokumenty na webu GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Pravidla FxCop implementovaná pomocí analyzátorů Roslyn na GitHubu](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
