---
title: Časovač | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1bed2715421948385a5b7eb1ddbbac064f3288b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778112"
---
# <a name="timer"></a>Časovač
*VSPerfCmd.exe* **Timer** možnost nastaví profilování událost, která je vzorkována na cykly hodin procesoru a volitelně změní počet cyklů v intervalu vzorkování z výchozí 10,000,000. Na 1GH (jeden gigahertz) procesor 10,000,000 hodiny cykly je přibližně 100 vzorků za sekundu. Minimální počet cyklů, které lze zadat, je 50 000.

 **Časovač** lze použít pouze při použití metody profilování vzorkování a lze jej použít pouze v příkazovém řádku, který obsahuje také možnost **Spustit** nebo **Připojit.**

 Ve výchozím nastavení je událost vzorkování profileru nastavena na cykly hodin procesoru a interval vzorkování je nastaven na 10 000 000. Možnosti **Časovač**, **PF**, **Sys**a **Čítač** umožňují nastavit vzorkovací událost a interval vzorkování. Možnost **GC** shromažďuje data paměti .NET při každé události přidělení a uvolňování paměti. Na příkazovém řádku lze zadat pouze jednu z těchto možností.

 Vzorkovací událost a interval vzorkování lze nastavit pouze v prvním příkazovém řádku, který obsahuje možnost **Spustit** nebo **Připojit.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parametry
 `Cycles`Celá hodnota, která určuje počet cyklů hodin procesoru v intervalu vzorkování. Pokud `Cycles` není zadán, interval je nastaven na 10 000 000. Zadejte hodnotu bez čárek.

## <a name="required-options"></a>Požadované možnosti
 **Časovač** lze zadat pouze na příkazovém řádku, který obsahuje jednu z následujících možností.

 **Spuštění:** `AppName` Spustí profiler a aplikaci určenou aplikací `AppName`.

 **Připojit:** `PID` Připojí profiler k procesu určenému ID procesu (`PID`).

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze zadat na stejném příkazovém řádku jako **timer**.

 **PF**[**:**`Events`] Nastaví událost vzorkování na chyby `Events`stránky a volitelně nastaví interval vzorkování na . Výchozí interval PF je 10.

 **Sys**[**:**`Events`] Nastaví událost vzorkování na volání `Events`operačního systému a volitelně nastaví interval vzorkování na . Výchozí interval Sys je 10.

 **Čítač**[**:**`Name,Reload,FriendlyName`] Nastaví událost `Name` vzorkování na `Reload`čítač výkonu procesoru určený a nastaví interval vzorkování na .

 **GC**[**:****{ Allocation**&#124;**Lifetime**}] Shromažďuje data paměti .NET. Ve výchozím nastavení (**Přidělení**) jsou data shromažďována při každé události přidělení paměti. Když je zadán parametr **Životnost,** data jsou také shromažďována při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak nastavit interval vzorkování profileru na 1 000 000 cyklů procesoru.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
