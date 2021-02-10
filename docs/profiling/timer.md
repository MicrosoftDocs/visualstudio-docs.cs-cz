---
title: Časovač | Microsoft Docs
description: Přečtěte si, jak možnost časovače VSPerfCmd.exe nastaví událost profilování, která je Navzorkovaná na časové cykly procesoru.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3aeffc3be3fee5d3460ddea340d8c4a216829e08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963156"
---
# <a name="timer"></a>Časovač
Možnost  **časovače** VSPerfCmd.exenastaví událost profilování, která je Navzorkovaná na časové cykly procesoru, a volitelně změní počet cyklů v intervalu vzorkování z výchozí hodnoty 10 000 000. Na procesorech frekvencí 1 GHz (jeden GHz) je 10 000 000 hodinových cyklů přibližně 100 vzorků za sekundu. Minimální počet cyklů, které lze zadat, je 50 000.

 **Časovač** se dá použít jenom v případě, že použijete metodu profilování vzorkování a dá se použít jenom v příkazovém řádku, který obsahuje taky možnost **Spustit** nebo **připojit** .

 Ve výchozím nastavení je událost vzorkování profileru nastavená na taktové cykly procesoru a interval vzorkování je nastaven na 10 000 000. Možnosti **časovač**, **PF**, **sys** a **čítač** umožňují nastavit událost vzorkování a interval vzorkování. Možnost **GC** shromažďuje data paměti .NET při každé události přidělení a uvolňování paměti. V příkazovém řádku lze zadat pouze jednu z těchto možností.

 Událost vzorkování a interval vzorkování lze nastavit pouze v prvním příkazovém řádku, který obsahuje možnost **Spustit** nebo **připojit** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parametry
 `Cycles` Celočíselná hodnota, která určuje počet hodinových cyklů procesoru v intervalu vzorkování. Pokud `Cycles` parametr není zadán, je interval nastaven na 10 000 000. Zadejte hodnotu bez čárek.

## <a name="required-options"></a>Požadované možnosti
 **Časovač** lze zadat pouze v příkazovém řádku, který obsahuje jednu z následujících možností.

 **Spustit:** `AppName` Spustí Profiler a aplikaci určenou nástrojem `AppName` .

 **Připojit:** `PID` Připojí profiler k procesu určenému IDENTIFIKÁTORem procesu ( `PID` ).

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze zadat na stejném příkazovém řádku jako **časovač**.

 **PF**[**:** `Events` ] nastaví událost vzorkování na chyby stránkování a volitelně nastaví interval vzorkování na `Events` . Výchozí interval BF je 10.

 **Sys**[**:** `Events` ] nastaví událost vzorkování na volání operačního systému a volitelně nastaví interval vzorkování na `Events` . Výchozí interval sys je 10.

 **Čítač**[**:** `Name,Reload,FriendlyName` ] nastaví událost vzorkování na čítač výkonu procesoru určený parametrem `Name` a nastaví interval vzorkování na `Reload` .

 **GC**[**:**{**Allocation**&#124;**životnost**}] shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**) se data shromažďují při každé události přidělení paměti. Při zadání parametru **životnosti** se data shromažďují také při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak nastavit interval vzorkování profileru na cyklus 1 000 000 procesorů.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
