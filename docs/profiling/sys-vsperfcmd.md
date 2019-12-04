---
title: Sys (VSPerfCmd) | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778177"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
Možnost *VSPerfCmd. exe* **sys** nastaví událost profilování, která je Navzorkovaná na události systémového volání (volání funkcí z profilované aplikace do operačního systému), a volitelně změní počet systémových volání v intervalu vzorkování od výchozí hodnoty 10.

 **Sys** se dá použít jenom v příkazovém řádku, který obsahuje taky možnost **Spustit** nebo **připojit** .

 Ve výchozím nastavení je událost vzorkování profileru nastavená na taktové cykly procesoru a interval vzorkování je nastaven na 10 000 000. Možnosti **časovač**, **PF**, **sys**a **čítač** umožňují nastavit událost vzorkování a interval vzorkování. Možnost **GC** shromažďuje data paměti .NET při každé události přidělení a uvolňování paměti. V příkazovém řádku lze zadat pouze jednu z těchto možností.

 Událost vzorkování a interval vzorkování lze nastavit pouze v prvním příkazovém řádku, který obsahuje možnost **Spustit** nebo **připojit** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events` celočíselnou hodnotu, která určuje počet událostí systémových volání v intervalu vzorkování. Pokud není zadaný `Events`, nastaví se interval na 10.

## <a name="required-options"></a>Požadované možnosti
 **Sys** vyžaduje jednu z následujících možností.

 **Spustit:** `AppName` spustí Profiler a aplikaci určenou v `AppName`.

 **Připojit:** `PID` připojí profiler k procesu určenému parametrem `PID`.

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze zadat na stejném příkazovém řádku jako **sys**.

 **PF**[ **:** `Events`] nastaví událost vzorkování na chyby stránkování a volitelně nastaví interval vzorkování na `Events`. Výchozí interval BF je 10.

 **Timer**[ **:** `Cycles`] nastaví událost vzorkování na časové cykly procesoru a volitelně nastaví interval vzorkování na `Cycles`. Výchozí interval časovače je 10 000 000.

 **Čítač:** `Name`[`,Reload`[`,FriendlyName`]] nastaví událost vzorkování na čítač výkonu procesoru určený `Name` a nastaví interval vzorkování na `Reload`.

 **GC**[ **:** {&#124;**disdoba**přidělení}] shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**) se data shromažďují při každé události přidělení paměti. Při zadání parametru **životnosti** se data shromažďují také při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak nastavit událost vzorkování profileru na systémová volání a jak nastavit interval vzorkování na 20 volání na vzorek.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
