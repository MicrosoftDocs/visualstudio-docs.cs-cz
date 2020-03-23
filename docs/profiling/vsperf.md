---
title: VSPerf | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 051c983920ddc80909d721e569c5efb5ecd33a7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779932"
---
# <a name="vsperf"></a>VSPerf
Pomocí nástroje příkazového řádku **VsPerf:**

1. Profil UPW aplikace z příkazového řádku, když Visual Studio není nainstalován v zařízení.

2. Profilovat desktopové aplikace systému Windows 8 a Windows Server 2012 pomocí metody profilování vzorkování.

   Další informace o možnostech profilování naleznete v [tématu Nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="uwp-apps-only"></a>Pouze aplikace UPW
 Tyto možnosti platí pouze pro aplikace UPW.

|||
|-|-|
|**/app:{Název_aplikace}**|Spustí profiler a čeká na spuštění zadané aplikace z nabídky Start.<br /><br /> Spuštěním `vsperf /listapps` zobrazíte název aplikace a packagefullname nainstalovaných aplikací.|
|**/package:{PackageFullName}**|Spustí profiler a čeká na spuštění zadané aplikace z nabídky Start.<br /><br /> Spuštěním `vsperf /listapps` zobrazíte název aplikace a packagefullname nainstalovaných aplikací.|
|**/js**|Vyžadováno pro profilování aplikací JavaScript.<br /><br /> Shromažďujte údaje o výkonu z aplikací JavaScript.<br /><br /> Používejte pouze s /package nebo /attach.|
|**/noclr**|Nepovinný parametr. Neshromažďujte data CLR.<br /><br /> Používejte pouze s /package nebo /attach.<br /><br /> Optimalizace, žádné spravované symboly se vyřeší.|
|**/listapps**|Seznam nainstalovaných názvů aplikací a PackageFullNames.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Pouze desktopové aplikace pro Windows 8 a Windows Server 2012
 Tyto možnosti nefungují v aplikacích UPW.

|||
|-|-|
|**/launch:{Spustitelný soubor}**|Spustí a zahájí profilování zadaného spustitelného souboru.|
|**/args:{Spustitelné argumenty}**|Určuje argumenty příkazového řádku, které mají předat cíl **/launch.**|
|**/konzole**|Spustí cíl **/launch** v novém příkazovém okně.|

## <a name="all-applications"></a>Všechny aplikace
 Tato možnost platí pro všechny aplikace pro Windows 8 nebo Windows Server 2012.

|||
|-|-|
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Shromažďuje data ze zadaných procesů.<br /><br /> Pomocí Správce úloh můžete zobrazit ID procesu (PID) a názvy spuštěných aplikací.|
|**/file:{Název_zprávy}**|Nepovinný parametr. Určuje výstupní soubor (přepíše existující soubor).<br /><br /> Používejte pouze s /package nebo /attach.|
|**/pauza**|Pozastavte sběr dat.|
|**/pokračovat**|Pokračovat ve shromažďování dat.|
|**/stop**|Zastavte shromažďování dat a ukončujte cílové procesy.|
|**/detach**|Zastavit shromažďování dat, ale nechat cílové procesy i nadále běžet.|
|**/stav**|Zobrazit stav profileru.|

## <a name="see-also"></a>Viz také
- [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
