---
title: PF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07ec6d636ec087386fdc9462ae09db55400957a9
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778411"
---
# <a name="pf"></a>PF
Možnost *VSPerfCmd. exe* **PF** nastaví událost profilování, která je Navzorkovaná na chyby stránkování, a volitelně změní počet chyb stránek v intervalu vzorkování z výchozí hodnoty 10.

> [!NOTE]
> V systémech 64 se nedá použít **PF** .

**PF** se dá použít jenom v příkazovém řádku, který obsahuje taky možnost **Spustit** nebo **připojit** .

 Ve výchozím nastavení je událost vzorkování nastavená na nezastavené časové cykly procesoru a interval vzorkování je nastaven na 10 000 000. Možnosti **časovač**, **PF**, **sys**a **čítač** umožňují nastavit ukázkovou událost a interval vzorkování. Možnost **GC** shromažďuje data paměti .NET při každé události přidělení a uvolňování paměti. V příkazovém řádku lze zadat pouze jednu z těchto možností.

 Událost vzorkování a interval vzorkování lze nastavit pouze v prvním příkazovém řádku, který obsahuje možnost **Spustit** nebo **připojit** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events` celočíselnou hodnotu, která určuje počet událostí selhání stránky v intervalu vzorkování. Pokud není zadaný `Events`, nastaví se interval na 10.

## <a name="required-options"></a>Požadované možnosti
 Parametr **PF** lze zadat pouze v příkazovém řádku, který obsahuje jednu z následujících možností.

 **Spustit:** `AppName` spustí Profiler a aplikaci určenou v APPNAME.

 **Připojit:** `PID` připojí profiler k procesu určenému parametrem APPNAME.

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze zadat na stejném příkazovém řádku jako **PF**.

 **Timer**[ **:** `Cycles`] nastaví událost vzorkování na časové cykly procesoru a volitelně nastaví interval vzorkování na `Cycles`. Výchozí interval časovače je 10 000 000.

 **Sys**[ **:** `Events`] nastaví událost vzorkování pro volání z profilované aplikace do jádra operačního systému (voláním) a volitelně nastaví interval vzorkování na `Events`. Výchozí interval sys je 10.

 **Čítač:** `Name`[`,Reload`[`,FriendlyName`]] nastaví událost vzorkování na čítač výkonu procesoru určený `Name` a nastaví interval vzorkování na `Reload`.

 **GC**[ **:** {&#124;**disdoba**přidělení}] shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**) se data shromažďují při každé události přidělení paměti. Při zadání parametru **životnosti** se data shromažďují také při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak nastavit událost vzorku profilování na chyby stránky a nastavit interval vzorkování na 20 chyb stránky.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
