---
title: VSPerf | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8042b228a481dc3d720d8b422963db41abbddcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533832"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj příkazového řádku **VsPerf** použijte k těmto akcím:  
  
1. Profilování aplikací pro Windows Store z příkazového řádku, když není v zařízení nainstalovaná aplikace Visual Studio.  
  
2. Profilujte aplikace pro stolní počítače s Windows 8 a aplikace Windows Serveru 2012 pomocí metody profilování vzorkování.  
  
   Další informace o možnostech profilace najdete v tématu [Nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>V tomto tématu  
 Toto téma popisuje možnosti, které můžete použít s `vsperf.exe` nástrojem příkazového řádku. Téma obsahuje následující části:  
  
 [Pouze aplikace pro Windows Store](#BKMK_windows_store_apps_only)  
  
 [Aplikace pro stolní počítače se systémem Windows 8 a Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Všechny aplikace](#BKMK_All_applications)  
  
## <a name="windows-store-apps-only"></a><a name="BKMK_windows_store_apps_only"></a>Pouze aplikace pro Windows Store  
 Tyto možnosti platí pouze pro aplikace pro Windows Store.  
  
|Možnost|Popis|  
|-|-|  
|**/App: {AppName}**|Spustí Profiler a počká na spuštění zadané aplikace z nabídky Start.<br /><br /> Spusťte `vsperf /listapps` pro zobrazení názvu aplikace a PackageFullName nainstalovaných aplikací.|  
|**/Package: {PackageFullName}**|Spustí Profiler a počká na spuštění zadané aplikace z nabídky Start.<br /><br /> Spusťte `vsperf /listapps` pro zobrazení názvu aplikace a PackageFullName nainstalovaných aplikací.|  
|**/js**|Vyžaduje se pro profilování aplikací JavaScriptu.<br /><br /> Shromažďovat údaje o výkonu z aplikací JavaScript<br /><br /> Používá se jenom s/Package nebo/Attach..|  
|**/noclr**|Nepovinný parametr. Neshromažďovat data CLR.<br /><br /> Používá se jenom s/Package nebo/Attach..<br /><br /> Optimalizace, žádné spravované symboly nebudou vyřešeny.|  
|**/listapps**|Vypíše názvy nainstalovaných aplikací a PackageFullNames.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a><a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a>Aplikace pro stolní počítače se systémem Windows 8 a Windows Server 2012  
 Tyto možnosti nefungují v aplikacích pro Windows Store.  
  
|Možnost|Popis|  
|-|-|  
|**/Lauch: {executable}**|Spustí a začne profilování zadaného spustitelného souboru.|  
|**/args: {ExecutableArguments}**|Určuje argumenty příkazového řádku pro předání cíle **/Lauch** .|  
|**/Console**|Spustí cíl **/Lauch** v novém příkazovém okně.|  
  
## <a name="all-applications"></a><a name="BKMK_All_applications"></a>Všechny aplikace  
 Tato možnost se vztahuje na všechny aplikace systému Windows 8 nebo Windows Server 2012.  
  
|Možnost|Popis|  
|-|-|  
|**/Attach: {PID&#124;Process} [, PID&#124;Process]...**|Shromažďuje data ze zadaných procesů.<br /><br /> Pomocí Správce úloh můžete zobrazit ID procesu (PID) a zpracovat názvy spuštěných aplikací.|  
|**/File: {Report}**|Nepovinný parametr. Určuje výstupní soubor (přepíše existující soubor).<br /><br /> Používá se jenom s/Package nebo/Attach..|  
|**/Pause**|Pozastavení sběru dat.|  
|**/Resume**|Obnovte shromažďování dat.|  
|**/stop**|Zastavení shromažďování dat a ukončení cílových procesů.|  
|**/detach**|Zastavte shromažďování dat, ale umožněte cílovým procesům pokračovat v běhu.|  
|**/status**|Zobrazit stav profileru.|  
  
## <a name="see-also"></a>Viz také  
 [Nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
