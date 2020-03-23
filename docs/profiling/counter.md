---
title: Počítadlo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e2f1684257ed39560fa0ea049d3296a6e45cdd7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779477"
---
# <a name="counter"></a>Čítač
Možnost **Čítač** shromažďuje data z čítačů výkonu procesoru (hardwaru).

- Při použití metody profilování vzorkování **čítač** určuje čítač výkonu na čipu a počet událostí čítače, které mají být používány jako interval vzorkování. Při použití vzorkování můžete zadat pouze jeden čítač.

- Pokud používáte metodu profilování instrumentace, počet událostí čítače, ke kterým došlo v intervalu mezi předchozí a aktuální událostí kolekce, je uveden jako samostatná pole v sestavách profileru. Více **možností čítače** lze zadat, pokud používáte instrumentaci.

  Každý typ procesoru má vlastní sadu čítačů výkonu hardwaru. Profiler definuje sadu obecných čítačů výkonu, které jsou společné pro téměř všechny procesory. Chcete-li v počítači uvést obecné čítače specifické pro procesor, použijte příkaz VSPerfCmd **QueryCounters.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametry
 `Name`Název čítače. Pomocí možnosti VSPerfCmd.exe **/QueryCounters** uveďte názvy dostupných čítačů v počítači.

 `Reload`Počet událostí čítače v intervalu vzorkování. Nepoužívejte s přístrojovou metodou.

 `FriendlyName`(Nepovinné) Řetězec, který se `Name` má použít místo v záhlaví sloupců sestavy profileru a zobrazení.

## <a name="required-options"></a>Požadované možnosti
 Možnost Čítač lze použít pouze s jednou z následujících možností:

 **Start:** `Trace` Inicializuje profiler pro použití metody instrumentace.

 **Spuštění:** `AppName` Spustí zadanou aplikaci a profiler. Profiler musí být inicializován, aby se použila metoda odběru vzorků.

 **Připojit:** `PID` Spustí profiler a připojí jej k procesu určenému ID procesu. Profiler musí být inicializován, aby se použila metoda odběru vzorků.

## <a name="example"></a>Příklad
 Příklad metody vzorkování ukazuje, jak vzorkovat aplikaci při každých 1000 výskytech čítače obecného profileru NonHaltedCycles.

 Příklad metody instrumentace ukazuje, jak inicializovat profiler shromažďovat události čítače L2InstructionFetches. Název čítače L2InstructionFetches je specifický pro procesor.

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
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
