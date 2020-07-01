---
title: VSPerf | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c58033e89742650dc097a7469cbf62d7b6168509
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520364"
---
# <a name="vsperf"></a>VSPerf
Nástroj příkazového řádku **VsPerf** použijte k těmto akcím:

1. Profilujte aplikace pro UWP z příkazového řádku, když v zařízení není nainstalovaná aplikace Visual Studio.

2. Profilujte aplikace pro stolní počítače s Windows 8 a aplikace Windows Serveru 2012 pomocí metody profilování vzorkování.

   Další informace o možnostech profilace najdete v tématu [Nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="uwp-apps-only"></a>Jenom aplikace pro UWP
 Tyto možnosti se vztahují jenom na aplikace pro UWP.

|Možnost|Popis|
|-|-|
|**/App: {AppName}**|Spustí Profiler a počká na spuštění zadané aplikace z nabídky Start.<br /><br /> Spusťte `vsperf /listapps` pro zobrazení názvu aplikace a PackageFullName nainstalovaných aplikací.|
|**/Package: {PackageFullName}**|Spustí Profiler a počká na spuštění zadané aplikace z nabídky Start.<br /><br /> Spusťte `vsperf /listapps` pro zobrazení názvu aplikace a PackageFullName nainstalovaných aplikací.|
|**/js**|Vyžaduje se pro profilování aplikací JavaScriptu.<br /><br /> Shromažďovat údaje o výkonu z aplikací JavaScript<br /><br /> Používá se jenom s/Package nebo/Attach..|
|**/noclr**|Nepovinný parametr. Neshromažďovat data CLR.<br /><br /> Používá se jenom s/Package nebo/Attach..<br /><br /> Optimalizace, žádné spravované symboly nebudou vyřešeny.|
|**/listapps**|Vypíše názvy nainstalovaných aplikací a PackageFullNames.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Aplikace pro stolní počítače se systémem Windows 8 a Windows Server 2012
 Tyto možnosti nefungují v aplikacích pro UWP.

|Možnost|Popis|
|-|-|
|**/Lauch: {executable}**|Spustí a začne profilování zadaného spustitelného souboru.|
|**/args: {ExecutableArguments}**|Určuje argumenty příkazového řádku pro předání cíle **/Lauch** .|
|**/Console**|Spustí cíl **/Lauch** v novém příkazovém okně.|

## <a name="all-applications"></a>Všechny aplikace
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

## <a name="see-also"></a>Viz také:
- [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
