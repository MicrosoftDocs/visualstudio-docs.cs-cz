---
title: Začínáme s analyzátory Roslyn | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 320f35d2a80f120d14f01b471449cd308ab30c8e
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348290"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Začínáme s analyzátory Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí analyzátorů kódu za provozu, na základě projektu v sadě Visual Studio dodávat autoři rozhraní API pro analýzu kódu specifického pro doménu jako součást své balíčky NuGet.  Protože tyto analyzátory využívají platformu kompilátoru .NET (s dřívějším kódovým označením Roslyn), může vést k upozornění ve vašem kódu při psaní ještě předtím, než jste dokončili řádku (žádné další čeká se na vytváření kódu ke zjišťování problémů).  Analyzátory můžou také to napravit automatické kód prostřednictvím žárovky řádku sady Visual Studio umožňuje vyčistit váš kód okamžitě zařízení surface

## <a name="getting-started"></a>Začínáme
[Analyzátory Roslyn živého kódu úvod a návody](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Přidání kódu řeší názorný postup: Zadejte uživatele opravy pro analyzátor problémů](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Úvod a návod Přednáška analyzátor reálného světa](http://channel9.msdn.com/events/Build/2015/3-725)

[Reálného světa Roslyn analyzátor](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , můžete se také podívat jako [komunikovat](http://channel9.msdn.com/events/Build/2015/3-725)

[Několik příkladů na Githubu, seskupených do tři druhy analyzátory](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Úvod a prohlídku několik analyzátory mluví](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Další zdroje
[Další dokumentace na webu GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Pravidla FxCop implementováno s analyzátory Roslyn na Githubu](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)

