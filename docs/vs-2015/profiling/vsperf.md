---
title: VSPerf | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 830aa028e8c34beb5fd6818c40ffcfc7f3fa461b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755257"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použití **VsPerf** nástroj příkazového řádku:  
  
1. Profilování aplikací Windows Store z příkazového řádku sady Visual Studio na něm není nainstalované na zařízení.  
  
2. Profil aplikace klasické pracovní plochy systému Windows 8 a Windows Server 2012 využívajících metoda profilování vzorkování.  
  
   Další informace o možnostech profilování, naleznete v tématu [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 Toto téma popisuje možnosti, které můžete používat `vsperf.exe` nástroj příkazového řádku. Téma obsahuje následující části:  
  
 [Jenom aplikace Windows Store](#BKMK_windows_store_apps_only)  
  
 [Aplikace klasické pracovní plochy systému Windows 8 a pouze aplikace systému Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Všechny aplikace](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Jenom aplikace Windows Store  
 Tyto možnosti platí pouze pro aplikace Windows Store.  
  
|||  
|-|-|  
|**/App: {AppName}**|Spuštění profileru a čeká na konkrétní aplikaci, která se má spustit z nabídky Start.<br /><br /> Spustit `vsperf /listapps` Chcete-li zobrazit aplikaci název a PackageFullName nainstalovaných aplikací.|  
|**/ balíčku: {PackageFullName}**|Spuštění profileru a čeká na konkrétní aplikaci, která se má spustit z nabídky Start.<br /><br /> Spustit `vsperf /listapps` Chcete-li zobrazit aplikaci název a PackageFullName nainstalovaných aplikací.|  
|**/JS**|Vyžaduje se pro profilování aplikací jazyka JavaScript.<br /><br /> Shromažďování dat výkonu z aplikací jazyka JavaScript.<br /><br /> Pouze pomocí/Package nebo / připojit.|  
|**/noclr**|Volitelné. Neshromažďují dat CLR.<br /><br /> Pouze pomocí/Package nebo / připojit.<br /><br /> Optimalizace, se vyřeší žádné spravované symboly.|  
|**/listapps**|Vypsání seznamu instalovaných názvů aplikací a PackageFullNames.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Aplikace klasické pracovní plochy systému Windows 8 a pouze aplikace systému Windows Server 2012  
 Tyto možnosti nebudou fungovat v aplikacích Windows Store.  
  
|||  
|-|-|  
|**/ spuštění: {spustitelný soubor}**|Spustí a začne profilace zadaný spustitelný soubor.|  
|**/ args: {ExecutableArguments}**|Určuje argumenty příkazového řádku k předání **/spuštění** cíl.|  
|**/ Console**|Spuštění **/spuštění** cíl v nové příkazové okno.|  
  
##  <a name="BKMK_All_applications"></a> Všechny aplikace  
 Tato možnost platí pro všechny aplikace systému Windows 8 nebo Windows Server 2012.  
  
|||  
|-|-|  
|**/ připojit: {PID&#124;ProcessName} [, PID&#124;ProcessName]...**|Shromažďuje data z konkrétních procesů.<br /><br /> Pomocí Správce úloh můžete zobrazit id procesu (PID) a názvy spuštěných aplikací procesu.|  
|**/ file:{ReportName}**|Volitelné. Určuje výstupní soubor (přepíše existující soubor).<br /><br /> Pouze pomocí/Package nebo / připojit.|  
|**/ Pause**|Shromažďování dat pozastavit.|  
|**/Resume**|Opět spustit shromažďování data.|  
|**/ stop**|Zastavit shromažďování dat a ukončit cílových procesů.|  
|**/ detach**|Zastavit shromažďování dat, ale nechat pokračovat ke spuštění cílových procesů.|  
|**/ Status**|Zobrazit stav profileru.|  
  
## <a name="see-also"></a>Viz také  
 [Nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)



