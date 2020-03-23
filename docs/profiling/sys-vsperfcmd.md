---
title: Sys (VSPerfCmd) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 435393ac536eb70f2f3f6d38b16eaab645848704
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778177"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
*Možnost VSPerfCmd.exe* **Sys** nastaví profilování událost, která je vzorkována na události volání systému (volání funkce z profilované aplikace do operačního systému) a volitelně změní počet volání systému v intervalu vzorkování z výchozí 10.

 **Sys** lze použít pouze v příkazovém řádku, který obsahuje také **možnost Spustit** nebo **Připojit.**

 Ve výchozím nastavení je událost vzorkování profileru nastavena na cykly hodin procesoru a interval vzorkování je nastaven na 10 000 000. Možnosti **Časovač**, **PF**, **Sys**a **Čítač** umožňují nastavit vzorkovací událost a interval vzorkování. Možnost **GC** shromažďuje data paměti .NET při každé události přidělení a uvolňování paměti. Na příkazovém řádku lze zadat pouze jednu z těchto možností.

 Vzorkovací událost a interval vzorkování lze nastavit pouze v prvním příkazovém řádku, který obsahuje možnost **Spustit** nebo **Připojit.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events`Celá hodnota, která určuje počet událostí systémového volání v intervalu vzorkování. Pokud `Events` není zadán, interval je nastaven na 10.

## <a name="required-options"></a>Požadované možnosti
 **Sys** vyžaduje jednu z následujících možností.

 **Spuštění:** `AppName` Spustí profiler a aplikaci určenou aplikací `AppName`.

 **Připojit:** `PID` Připojí profiler k procesu `PID`určenému .

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze zadat na stejném příkazovém řádku jako **sys**.

 **PF**[**:**`Events`] Nastaví událost vzorkování na chyby `Events`stránky a volitelně nastaví interval vzorkování na . Výchozí interval PF je 10.

 **Časovač**[**:**`Cycles`] Nastaví událost vzorkování na cykly `Cycles`hodin procesoru a volitelně nastaví interval vzorkování na . Výchozí interval časovače je 10 000 000.

 **Čítač:** `Name`[`,Reload`[`,FriendlyName`]] Nastaví událost `Name` vzorkování na `Reload`čítač výkonu procesoru určený a nastaví interval vzorkování na .

 **GC**[**:****{ Allocation**&#124;**Lifetime**}] Shromažďuje data paměti .NET. Ve výchozím nastavení (**Přidělení**) jsou data shromažďována při každé události přidělení paměti. Když je zadán parametr **Životnost,** data jsou také shromažďována při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak nastavit událost vzorkování profileru na systémová volání a jak nastavit interval vzorkování na 20 volání na vzorek.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
