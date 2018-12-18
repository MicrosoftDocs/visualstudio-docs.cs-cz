---
title: Přidání dat interakce vrstev z příkazového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3912e823a6e6ee32488fcda94616aef414d3d22
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775300"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Přidání dat interakce vrstev z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilování interakce vrstev poskytuje další informace o spuštění s úspěšností synchronní [!INCLUDE[vstecado](../includes/vstecado-md.md)] volání funkce víceúrovňových aplikací, které komunikují po jedné nebo víc databází.  
  
 **Windows 8 a Windows Server 2012**  
  
 Ke shromažďování dat interakce vrstev pro aplikace klasické pracovní plochy systému Windows 8 a Windows Server 2012 aplikací musí použít metody instrumentace. Shromažďování dat interakce vrstev v aplikacích Windows Store není podporován.  
  
 **Edice sady Visual Studio**  
  
 Profilování interakce vrstev lze shromažďovat pomocí sady [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Nicméně data profilace interakce vrstev lze zobrazit pouze v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Shromažďování dat TIP na vzdáleném počítači**  
  
 Ke shromažďování dat interakce vrstev ve vzdáleném počítači, je nutné zkopírovat **vs\_profiler\_**_\<platformy >_ **\_**  _\<Jazyk >_**.exe** soubor _VSInstallDir %_**\Team Tools\Performance Tools\Setups**složky sady Visual Studio počítače ke vzdálenému počítači a nainstalujte ho. Nelze použít v nástrojů pro profilaci [Visual Studio Remote Tools](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) stažení balíčku.  
  
 **TIP sestavy**  
  
 Dat interakce vrstev lze zobrazit pouze v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] integrovaného vývojového prostředí. Interakce vrstev souborovému sestavy prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Přidání dat interakce vrstev s VSPerfCmd  
 Nástroj příkazového řádku příkaz VSPerfASPNETCmd vám umožní přístup k dokončení funkce dostupná v nástrojích pro profilaci. Chcete-li přidat data shromážděná pomocí, VSPerfCmd profilace interakce vrstev, musíte použít **VSPerfCLREnv** nástroj pro nastavení a odebrání proměnné prostředí, která umožňuje dat interakce vrstev. Možnosti, které zadáte a postupy potřebné ke shromažďování dat závisí na typu aplikace, který profilujete.  
  
### <a name="profiling-stand-alone-applications"></a>Profilace samostatných aplikací  
 Přidání dat interakce vrstev do aplikace, která se spustí jiný proces, jako jsou aplikace klasické pracovní plochy Windows, která umožňuje synchronní [!INCLUDE[vstecado](../includes/vstecado-md.md)] volání do databáze systému SQL Server, je použít **VSPerfClrEnv /InteractionOn** možnost nastavit proměnné prostředí a **VSPerfClrEnv /InteractionOff** možností jejich odebrání.  
  
 V následujícím příkladu je pomocí metody instrumentace profilované aplikace klasické pracovní plochy Windows a shromažďovaných dat interakce vrstev.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Příklad aplikace klasické pracovní plochy Windows pro profilaci  
  
1. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na **všechny programy**a pak na **Příslušenství**. Klikněte pravým tlačítkem na **příkazového řádku**a potom klikněte na tlačítko **spustit jako správce**.  
  
2. Inicializace proměnných prostředí TIP a profilování rozhraní .NET. Zadejte následující příkazy:  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. Spusťte profiler. Zadejte následující příkaz:  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. Spusťte aplikaci pomocí VSPerfCmd. Zadejte následující příkaz:  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. Výkon aplikace ke shromažďování dat profilování a poté ukončete aplikaci běžným způsobem.  
  
6. Vyčistěte proměnné prostředí pro popis TLAČÍTKA. Zadejte následující příkaz:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Další informace najdete v tématu [profilování aplikací samostatného](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Profilace služeb  
 Do profilu služby, včetně [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikací, použijte **VSPerfClrEnv /GlobalInteractionOn** možnost nastavit proměnné prostředí a **VSPerfClrEnv /GlobalInteractionOff** možností jejich odebrání.  
  
 Pokud provádíte profilaci služeb, včetně [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webových aplikací, je často potřeba počítač restartovat, aby povolit profilaci.  
  
 V následujícím příkladu služba Windows je profilována metodou instrumenation a shromažďovaných dat interakce vrstev.  
  
##### <a name="profiling-a-windows-service-example"></a>Příklad služby Windows pro profilaci  
  
1. V případě potřeby nainstalujte službu.  
  
2. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na **všechny programy**a pak na **Příslušenství**. Klikněte pravým tlačítkem na **příkazového řádku**a potom klikněte na tlačítko **spustit jako správce**.  
  
3. Inicializujte proměnné prostředí profilování rozhraní .NET. Zadejte následující příkaz:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. Inicializujte proměnné prostředí TIP. Zadejte následující příkaz  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Restartujte počítač a zaregistrovat proměnné prostředí.  
  
6. Otevřete okno příkazového řádku s oprávněními správce.  
  
7. Spusťte profiler. Zadejte následující příkaz:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. V případě potřeby spusťte službu.  
  
9. Připojení profileru ke službě. Zadejte následující příkaz:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Výkon služby a shromažďování dat profilace.  
  
11. Ukončete profiler. Zadejte následující příkaz:  
  
     `vsperfcmd /detach`  
  
12. Vymažte .NET a TIP proměnných prostředí profilování. Zadejte následující příkaz:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Restartujte počítač a zaregistrovat proměnné prostředí nezaškrtnuté.  
  
    Další informace naleznete v jednom z následujících témat:  
  
    [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Profilace služeb](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Přidání dat interakce vrstev stránek pomocí VSPerfASPNETCmd  
 Nástroj příkazového řádku příkaz VSPerfASPNETCmd vám umožní snadno profilu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace. Ve srovnání s **VSPerfCmd** nástroj příkazového řádku, možnosti jsou zmenšeny, musí být nastaveny žádné proměnné prostředí a restartování počítače se nevyžaduje. Tyto funkce VSPerfASPNETCmd shromažďování dat interakce vrstev výjimečně usnadňují.  
  
 Chcete-li přidat data shromážděná pomocí VSPerfASPNETCmd profilace interakce vrstev, přidejte **/TIP** možnost příkazového řádku. Například použijte následující příkazový řádek ke shromažďování dat interakce vrstev pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci pomocí metody instrumentace:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Další informace o VSPerfASPNETCmd najdete v tématu [rychlé webových profilů stránek pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).



