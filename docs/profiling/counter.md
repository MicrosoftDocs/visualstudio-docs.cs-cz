---
title: Čítač | Microsoft Docs
description: Přečtěte si o možnosti čítače VSPerfCmd.exe. Určuje interval vzorkování nebo měření intervalů událostí při profilaci instrumentace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 85ed799cac54d630dfff1b285d3f2257e5eb99b5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720693"
---
# <a name="counter"></a>Čítač
Možnost **čítač** shromažďuje data z čítačů výkonu procesoru (hardware).

- Při použití metody profilace vzorkování Určuje **čítač** čítač výkonu na čipu a počet událostí čítače, které se mají použít jako interval vzorkování. Když používáte vzorkování, můžete zadat jenom jeden čítač.

- Pokud používáte metodu profilace instrumentace, počet událostí čítače, ke kterým došlo v intervalu mezi předchozími a aktuálními událostmi kolekce, je v sestavách profileru uveden jako samostatná pole. Při použití instrumentace lze zadat více možností **čítače** .

  Každý typ procesoru má vlastní sadu čítačů výkonu hardwaru. Profiler definuje sadu obecných čítačů výkonu, které jsou společné pro téměř všechny procesory. K vypsání obecných a specifických čítačů pro konkrétní procesor v počítači použijte příkaz VSPerfCmd **QueryCounters** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametry
 `Name` Název čítače. K vypsání názvů čítačů dostupných v počítači použijte možnost VSPerfCmd.exe **/QueryCounters** .

 `Reload` Počet událostí čítače v intervalu vzorkování. Nepoužívejte s metodou instrumentace.

 `FriendlyName` Volitelné Řetězec, který má být použit místo `Name` v záhlavích sloupců sestav a zobrazení profileru.

## <a name="required-options"></a>Požadované možnosti
 Možnost čítače lze použít pouze s jednou z následujících možností:

 **Začátek:** `Trace` Inicializuje Profiler, aby používal metodu instrumentace.

 **Spustit:** `AppName` Spustí zadanou aplikaci a Profiler. Profiler je nutné inicializovat pro použití metody vzorkování.

 **Připojit:** `PID` Spustí Profiler a připojí ho k procesu určenému ID procesu. Profiler je nutné inicializovat pro použití metody vzorkování.

## <a name="example"></a>Příklad
 Ukázka metody vzorkování ukazuje, jak vzorkovat aplikaci při každém 1000 výskytech obecného čítače profileru NonHaltedCycles.

 Příklad metody instrumentace ukazuje, jak inicializovat profiler pro shromažďování událostí čítače L2InstructionFetches. Název čítače L2InstructionFetches je specifický pro procesor.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
