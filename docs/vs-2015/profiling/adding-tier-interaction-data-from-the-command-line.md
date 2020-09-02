---
title: Přidání dat interakce vrstev z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 369c5b75780e9d557dedbde60b5b584c8b3345b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705838"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Přidání dat interakce vrstev z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilace interakce vrstev poskytuje další informace o době spuštění synchronních [!INCLUDE[vstecado](../includes/vstecado-md.md)] volání ve funkcích vícevrstvých aplikací, které komunikují s jednou nebo více databázemi.  
  
 **Windows 8 a Windows Server 2012**  
  
 Pro shromažďování dat interakce vrstev v aplikacích pro stolní počítače se systémem Windows 8 a Windows Server 2012 je nutné použít metodu instrumentace. Shromažďování dat interakce vrstev v aplikacích pro Windows Store se nepodporuje.  
  
 **Edice sady Visual Studio**  
  
 Profilování interakce vrstev lze shromažďovat pomocí sady [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Data profilování interakce vrstev ale můžete zobrazit jenom v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
 **Shromažďování dat s tipem na vzdáleném počítači**  
  
 Chcete-li shromažďovat data o interakcích vrstev na vzdáleném počítači, je nutné zkopírovat soubor **vs \_ Profiler \_ ** _\<Platform>_ **\_** _\<Language>_ **. exe** ze složky _% VSINSTALLDIR%_**\Team Tools\Performance Tools\Setups** počítače Visual Studio do vzdáleného počítače a nainstalovat jej. Nástroje pro profilaci nelze použít v balíčku ke stažení pro [vzdálené nástroje sady Visual Studio](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
 **Sestavy tipů**  
  
 Data interakce vrstev se dají zobrazit jenom v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] integrovaném vývojovém prostředí. Sestavy interakce na úrovni souborů prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Přidání dat interakce vrstev pomocí VSPerfCmd  
 Nástroj příkazového řádku VSPerfASPNETCmd umožňuje přístup k kompletním funkcím, které jsou k dispozici v Nástroje pro profilaci. Chcete-li přidat interakci vrstev do dat profilace shromážděných pomocí VSPerfCmd, je nutné použít nástroj **VSPerfCLREnv** k nastavení a odebrání proměnných prostředí, které povolují data interakce vrstev. Možnosti, které zadáte, a postupy vyžadované ke shromažďování dat závisí na typu aplikace, kterou vytváříte profilování.  
  
### <a name="profiling-stand-alone-applications"></a>Profilace samostatných aplikací  
 Chcete-li přidat data interakce vrstev do aplikace, kterou nespouští jiný proces, jako je například aplikace klasické pracovní plochy systému Windows, která provádí synchronní [!INCLUDE[vstecado](../includes/vstecado-md.md)] volání databáze SQLServer, použijte možnost **VSPerfCLREnv/InteractionOn** pro nastavení proměnných prostředí a možnost **VSPerfCLREnv/InteractionOff** pro jejich odebrání.  
  
 V následujícím příkladu je aplikace klasické pracovní plochy systému Windows profilovaná pomocí metody instrumentace a dat interakce vrstev.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Příklad profilace desktopové aplikace pro Windows  
  
1. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na příkaz **všechny programy**a pak na položku **příslušenství**. Klikněte pravým tlačítkem myši na **příkazový řádek**a pak klikněte na **Spustit jako správce**.  
  
2. Inicializujte profilaci .NET a proměnné prostředí TIP. Zadejte následující příkazy:  
  
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
  
5. Pocvičením aplikace Shromážděte data profilace a pak aplikaci zavřete běžným způsobem.  
  
6. Vymažte proměnné prostředí s tipem. Zadejte následující příkaz:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Další informace najdete v tématu [profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Služby profilace  
 K profilování služeb, včetně [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikací, použijte možnost **VSPerfCLREnv/GlobalInteractionOn** k nastavení proměnných prostředí a možnost **VSPerfCLREnv/GlobalInteractionOff** k jejich odebrání.  
  
 Pokud používáte služby profilování, včetně [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webových aplikací, budete často muset restartovat počítač, aby bylo možné profilování povolit.  
  
 V následujícím příkladu je služba systému Windows profilovaná pomocí metody instrumenation a jsou shromažďována data interakce vrstev.  
  
##### <a name="profiling-a-windows-service-example"></a>Příklad profilace služby systému Windows  
  
1. V případě potřeby nainstalujte službu.  
  
2. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na příkaz **všechny programy**a pak na položku **příslušenství**. Klikněte pravým tlačítkem myši na **příkazový řádek**a pak klikněte na **Spustit jako správce**.  
  
3. Inicializujte proměnné prostředí pro profilování .NET. Zadejte následující příkaz:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. Inicializujte proměnné prostředí s tipem. Zadejte následující příkaz  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Chcete-li zaregistrovat proměnné prostředí, restartujte počítač.  
  
6. Otevřete okno příkazového řádku s oprávněními správce.  
  
7. Spusťte profiler. Zadejte následující příkaz:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. V případě potřeby službu spusťte.  
  
9. Připojte profiler ke službě. Zadejte následující příkaz:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Cvičení služby a shromažďování dat profilace.  
  
11. Zastavte Profiler. Zadejte následující příkaz:  
  
     `vsperfcmd /detach`  
  
12. Vymažte proměnné prostředí pro profilování rozhraní .NET a TIP. Zadejte následující příkaz:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Restartujte počítač pro registraci vymazaných proměnných prostředí.  
  
    Další informace naleznete v jednom z následujících témat:  
  
    [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Profilace služeb](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Přidání dat interakce vrstev pomocí VSPerfASPNETCmd  
 Nástroj příkazového řádku VSPerfASPNETCmd umožňuje snadno profilovat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace. V porovnání s nástrojem příkazového řádku **VSPerfCmd** se možnosti sníží, žádné proměnné prostředí není potřeba nastavit a restartování počítače se nevyžaduje. Díky těmto funkcím VSPerfASPNETCmd je shromažďování dat interakce vrstev výjimečně snadné.  
  
 Chcete-li přidat interakci vrstvy k datům profilování shromážděným pomocí VSPerfASPNETCmd, přidejte do příkazového řádku možnost **/Tip** . Pomocí následujícího příkazového řádku můžete například shromažďovat data interakce vrstev pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci pomocí metody instrumentace:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Další informace o VSPerfASPNETCmd najdete v tématu [rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
