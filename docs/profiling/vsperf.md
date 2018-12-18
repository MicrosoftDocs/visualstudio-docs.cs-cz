---
title: VSPerf | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c841e6930db8f65aaf93c314359656689ecfd1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903540"
---
# <a name="vsperf"></a>VSPerf
Použití **VsPerf** nástroj příkazového řádku:  
  
1. Profilování aplikací UPW z příkazového řádku sady Visual Studio na něm není nainstalované na zařízení.  
  
2. Profil aplikace klasické pracovní plochy systému Windows 8 a Windows Server 2012 využívajících metoda profilování vzorkování.  
  
   Další informace o možnostech profilování, naleznete v tématu [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="uwp-apps-only"></a>V aplikacích pro UWP  
 Tyto možnosti platí pouze pro aplikace UWP.  
  
|||  
|-|-|  
|**/App: {AppName}**|Spuštění profileru a čeká na konkrétní aplikaci, která se má spustit z nabídky Start.<br /><br /> Spustit `vsperf /listapps` Chcete-li zobrazit aplikaci název a PackageFullName nainstalovaných aplikací.|  
|**/ balíčku: {PackageFullName}**|Spuštění profileru a čeká na konkrétní aplikaci, která se má spustit z nabídky Start.<br /><br /> Spustit `vsperf /listapps` Chcete-li zobrazit aplikaci název a PackageFullName nainstalovaných aplikací.|  
|**/JS**|Vyžaduje se pro profilování aplikací jazyka JavaScript.<br /><br /> Shromažďování dat výkonu z aplikací jazyka JavaScript.<br /><br /> Pouze pomocí/Package nebo / připojit.|  
|**/noclr**|Volitelné. Neshromažďují dat CLR.<br /><br /> Pouze pomocí/Package nebo / připojit.<br /><br /> Optimalizace, se vyřeší žádné spravované symboly.|  
|**/listapps**|Vypsání seznamu instalovaných názvů aplikací a PackageFullNames.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Aplikace klasické pracovní plochy systému Windows 8 a pouze aplikace systému Windows Server 2012  
 Tyto možnosti nelze použít u aplikací pro UWP.  
  
|||  
|-|-|  
|**/ spuštění: {spustitelný soubor}**|Spustí a začne profilace zadaný spustitelný soubor.|  
|**/ args: {ExecutableArguments}**|Určuje argumenty příkazového řádku k předání **/spuštění** cíl.|  
|**/ Console**|Spuštění **/spuštění** cíl v nové příkazové okno.|  
  
## <a name="all-applications"></a>Všechny aplikace  
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
  
## <a name="see-also"></a>Viz také:  
 [Nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)