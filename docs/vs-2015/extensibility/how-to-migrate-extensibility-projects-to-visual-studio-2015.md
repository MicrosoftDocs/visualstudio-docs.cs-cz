---
title: 'Postupy: migrace rozšiřujících projektů do sady Visual Studio 2015 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46b48370847cbb2cf8b171342aff9baf38c40a22
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295557"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Postupy: migrace rozšiřujících projektů do sady Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tady je postup, jak upgradovat rozšíření.  
  
> [!IMPORTANT]
> Pokud máte v úmyslu zachovat verzi vašeho řešení rozšíření pro starší verzi sady Visual Studio, nezapomeňte před upgradem vytvořit kopii. Může být obtížné vrátit upgradovanou verzi do předchozího stavu.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Upgrade řešení rozšiřitelnosti  
  
1. Pomocí kopie, kterou chcete upgradovat, otevřete ji v nové verzi. Doporučujeme vám, abyste upgrade nevratný.  
  
2. Po dokončení upgradu změňte cestu k externímu programu na novou verzi nástroje devenv. exe. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a pak zvolte **vlastnosti**. Na kartě **ladění** vyhledejte textové pole podle **spuštění externího programu** a změňte cestu k souboru devenv. exe na cestu sady Visual Studio 2015, která by měla vypadat přibližně takto:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE\devenv.exe**  
  
3. Přidejte odkaz na Microsoft. VisualStudio. Shell. 14.0. dll. (Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a zvolte možnost **Přidat nebo odkaz**. Vyberte kartu **rozšíření** a pak zkontrolujte **Microsoft. VisualStudio. Shell. 14.0**.)  
  
4. Sestavte řešení. Sestavené soubory jsou nasazeny do:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< jméno autora\>\\< název projektu\>\\< projektu verze\>** \\.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Aktualizace projektu rozšíření na referenční sestavení sady NuGet VS SDK  
  
1. Určete referenční sestavení sady VS SDK, které projekt potřebuje.  V **Průzkumník řešení**rozbalte uzel **odkazy** projektu a zkontrolujte seznam odkazů na projekt.  Sada VS SDK odkazuje na sestavení bude mít v názvu předponu **Microsoft. VisualStudio** (například: Microsoft. VisualStudio. Shell. 14.0).  
  
2. Z projektu odeberte referenční sestavení sady VS SDK, a to tak, že je vyberete, kliknete pravým tlačítkem a **odeberete**.  
  
3. Přidejte verze NuGet referenčních sestavení sady VS SDK.  I když je v uzlu **odkazy na Průzkumník řešení** , otevřete okno **Spravovat balíčky NuGet...** Dialogové okno.  Pokud chcete získat další informace o tomto dialogovém okně, přečtěte si téma [Správa balíčků NuGet pomocí tohoto dialogového okna](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio). Referenční sestavení sady VS SDK jsou publikována v [NuGet.org](https://www.nuget.org/) pomocí [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. Jako **zdroj balíčku**použijte **NuGet.org** , vyhledejte název balíčku NuGet, který odpovídá požadovanému referenčnímu sestavení (například: Microsoft. VisualStudio. Shell. 14.0) a nainstalujte ho do projektu.  NuGet může přidat několik referenčních sestavení, aby bylo možné splnit počáteční závislosti sestavení.  
  
     Pokud chcete, můžete přidat všechna referenční sestavení sady VS SDK najednou instalací [meta balíčku](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)sady vs SDK.  
  
5. Můžete také přepnout na použití verze NuGet nástrojů sestavení sady VS SDK. Tento balíček NuGet je [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) a po jeho přidání do projektu budou zahrnuty potřebné nástroje a cílové soubory, které vám umožní sestavit projekt rozšiřitelnosti na počítači bez nainstalované sady vs SDK.  
  
> [!NOTE]
> Není nutné aktualizovat existující projekty rozšíření tak, aby používaly referenční sestavení a nástroje NuGet.  Mohou pokračovat v sestavování pomocí referenčních sestavení a nástrojů, které jsou nainstalovány se sadou VS SDK.
