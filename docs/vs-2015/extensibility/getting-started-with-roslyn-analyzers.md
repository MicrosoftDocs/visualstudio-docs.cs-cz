---
title: Začínáme s analyzátory Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300014"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Začínáme s analyzátory Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S živými analyzátory kódu založenými na projektech v aplikaci Visual Studio můžou autoři rozhraní API dodávat analýzu kódu specifickou pro doménu jako součást jejich balíčků NuGet.  Vzhledem k tomu, že tyto analyzátory využívají .NET Compiler Platform (kód s názvem "Roslyn"), mohou ve vašem kódu při psaní vydávat upozornění, i když jste dokončili řádek (nečekáte na sestavení kódu pro zjišťování problémů).  Analyzátory mohou také automaticky opravovat opravy kódu prostřednictvím výzvy k vyčistění kódu hned po výzvě Visual Studio Light.

## <a name="getting-started"></a>Začínáme
[Úvodní a návod pro Roslyn Live Code Analyzer](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Přidání návodu k opravám kódu: poskytnutí oprav pro problémy s analyzátorem pro uživatele](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Úvod a návody k programu Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , který můžete také sledovat jako [rozhovor](https://channel9.msdn.com/events/Build/2015/3-725)

[Několik příkladů na GitHubu, seskupené do tří druhů analyzátorů](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Úvod do několika rozhovorů analyzátorů a jejich prohlídka](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Další prostředky
[Další dokumentace na webu GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Pravidla FxCop implementovaná pomocí analyzátorů Roslyn na GitHubu](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
