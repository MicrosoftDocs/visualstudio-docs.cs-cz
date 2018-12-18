---
title: 'Postupy: aktualizace rozšíření sady Visual Studio | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bf951215dfb4f6837c157a7b8510fba2d09f140
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500184"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Postupy: aktualizace rozšíření sady Visual Studio
Rozšíření sady Visual Studio můžete aktualizovat v systému s použitím **rozšíření a aktualizace** k instalaci aktualizované verze. Pokud vytvoříte aktualizovanou verzi rozšíření, můžete ho místo při aktualizaci zvyšující číslo verze v manifestu VSIX.  
  
 Aktualizace se nainstalují při manifest VSIX příchozí rozšíření má stejnou `ID` jako je nainstalovaný a vyšší `Version` číslo. Pokud `Version` číslo je stejná nebo nižší, nejde nainstalovat balíček. Pokud `ID` se hodnoty neshodují, je balíček, který dosud není nainstalován rozpoznán jako samostatné rozšíření.  
  
 Abyste líp zabránili konfliktům během vývoje, doporučujeme, odinstalovat starší verze rozšíření probíhá a také odinstalujete nebo další potenciálně konfliktním rozšíření zakázat.  
  
## <a name="to-update-an-extension-on-your-system"></a>Chcete-li aktualizovat rozšíření ve vašem systému  
  
1.  Na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.  
  
2.  V levém podokně klikněte na tlačítko **aktualizace**.  
  
3.  V prostředním podokně klikněte na aktualizaci, kterou chcete nainstalovat.  
  
     Číslo verze aktualizované rozšíření se zobrazí v pravém podokně, společně s další informace.  
  
4.  Dole v pravém podokně klikněte na tlačítko **aktualizace**.  
  
## <a name="to-publish-an-update-of-an-extension"></a>Chcete-li publikovat aktualizace rozšíření  
  
1.  V sadě Visual Studio otevřete řešení rozšíření, které chcete aktualizovat. Proveďte požadované změny.  
  
    > [!IMPORTANT]
    >  Hodnota bez znaménka že všechna rozšíření uživatele aktualizován automaticky. Měli byste vždy podepsat vaše rozšíření.  
  
2.  V **Průzkumníka řešení**, otevřete *source.extension.manifest*.  
  
3.  V Návrháři manifestu zvýšit hodnotu čísla v **verze** pole.  
  
4.  Uložte řešení a sestavte ho.  
  
5.  Nahrát nový *VSIX* souboru (v * \bin\Debug\* složka projektu) k [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) webu.  
  
     Když se otevře uživatel, který má starší verzi rozšíření **rozšíření a aktualizace**, nová verze zobrazí v **aktualizace** seznamu, za předpokladu, že nástroj je nastavena automaticky vyhledat aktualizace.  
  
     Můžete povolit nebo zakázat automatické zjišťování aktualizací v dolní části **aktualizace** podokně (**povolí nebo zakáže automatické zjišťování dostupných aktualizací**), které změny **vyhledat aktualizace** nastavení **nástroje** > **možnosti** > **prostředí**  >  **Rozšíření a aktualizace**.  
  
    > [!NOTE]
    >  Od verze Visual Studio 2015 Update 2, můžete zadat (v **nástroje** > **možnosti** > **prostředí**  >  **Rozšíření a aktualizace**) určuje, zda chcete automatické aktualizace pro rozšíření vázaná na uživatele, všechna rozšíření uživatele nebo obě (výchozí nastavení).  
  
## <a name="see-also"></a>Viz také:  
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)