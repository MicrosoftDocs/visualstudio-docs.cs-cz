---
title: 'Postupy: migrace projektů rozšíření do sady Visual Studio 2015 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 564e279d259cae879ca2925eed3309c30d7513db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785154"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Postupy: migrace projektů rozšíření do sady Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tady je postup upgradu rozšíření.  
  
> [!IMPORTANT]
>  Pokud máte v úmyslu spravovat verze řešení rozšíření pro starší verzi sady Visual Studio, je potřeba vytvořit kopii, před provedením upgradu. Může být obtížné upgradovanou verzi vrátit do předchozího stavu.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Upgradovat řešení rozšiřitelnosti  
  
1.  Pomocí dané kopie, kterou chcete upgradovat, otevřete ho v nové verzi. Budete informováni, že upgrade je nevratná operace.  
  
2.  Po dokončení upgradu, změňte cestu k externí program na novou verzi devenv.exe. Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení**, klikněte na tlačítko **vlastnosti**. V **ladění** kartu, najít textového pole ve **externí program Start** a změňte cestu devenv.exe na cestu systému Visual Studio 2015, která by měl vypadat asi takhle nějak.:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Přidejte odkaz na Microsoft.VisualStudio.Shell.14.0.dll. (Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a klikněte na tlačítko **přidat / Reference**. Vyberte **rozšíření** kartu a potom zkontrolujte **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Sestavte řešení. Vytvořené soubory jsou nasazené na:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< vytvářet název\>\\< název projektu\>\\< verze projektu\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Chcete-li aktualizovat projekt rozšiřitelnosti NuGet VS SDK referenčních sestavení  
  
1.  Určete referenční sestavení sady SDK pro VS, které projekt potřebuje.  V **Průzkumníka řešení**, rozbalte položku projektu **odkazy** uzlu a projděte si seznam odkazů na projekt.  Odkazy na sestavení sady SDK pro VS budou mít předponu **Microsoft.VisualStudio** v názvu (například: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Odebrat z projektu VS SDK referenční sestavení tak, že je vyberete, klikněte pravým tlačítkem myši a **odebrat**.  
  
3.  Přidání verze NuGet referenčních sestavení sady SDK pro VS.  Pokud máte **odkazy Průzkumníka řešení** uzel, otevřete **spravovat balíčky NuGet...** Dialogové okno.  Pokud chcete získat další informace o tomto dialogovém okně, přečtěte si téma [spravovat NuGet balíčky pomocí dialogového okna](http://docs.nuget.org/Consume/Package-Manager-Dialog). Referenční sestavení sady SDK pro VS jsou publikovány v [nuget.org](http://www.nuget.org) podle [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Pomocí **nuget.org** jako vaše **zdroj balíčku**, vyhledejte název balíčku NuGet, který by odpovídal požadovaný odkaz na sestavení (například: Microsoft.VisualStudio.Shell.14.0) a nainstalujte ho v vaší projekt.  NuGet může přidání více odkazů na sestavení splníte závislosti počáteční sestavení.  
  
     Pokud dáváte přednost, můžete přidat všechny referenční sestavení sady SDK pro VS najednou nainstalováním sady SDK pro VS [Meta balíčku](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Můžete také přejít na verze NuGet nástroje sestavení sady SDK pro VS. Tento balíček NuGet je [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) a jednou přidán do projektu bude obsahovat potřebné nástroje a cílové soubory umožňují vytvářet rozšíření projektu v počítači bez nainstalované VS SDK.  
  
> [!NOTE]
>  Není vyžadováno, že aktualizujete existující projekty rozšiřitelnosti použít NuGet referenčních sestavení a nástroje.  Může i nadále sestavení pomocí referenčních sestavení a nástroje, které jsou nainstalovány se sadou SDK pro VS.

