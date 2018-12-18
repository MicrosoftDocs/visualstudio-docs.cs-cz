---
title: Čítač | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d0d15c404284dfb40105f7a52cb23aef132f3a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764938"
---
# <a name="counter"></a>Čítač
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Čítač** možnost shromažďuje data z čítače výkonu procesoru (hardwaru).  
  
- Při použití metoda profilování vzorkování **čítač** určuje čítač výkonu na čipu a počet událostí čítače pro použití jako interval vzorkování. Při použití vzorkování, můžete zadat pouze jeden čítač.  
  
- Při použití metoda profilace instrumentace, číslo události čítače, ke kterým došlo v intervalu mezi událostmi předchozích a aktuálních kolekce jsou uvedené jako samostatná pole v sestavách profileru. Více **čítač** možnosti lze zadat, pokud používáte instrumentace.  
  
  Každý typ procesoru má svou vlastní sadu čítačů výkonu hardwaru. Profiler definuje sadu čítačů obecný výkonu, které jsou společné pro téměř všechny procesory. Chcete-li seznam čítačů obecný a specifické pro procesor v počítači, použijte příkazu vsperfcmd proveďte **QueryCounters** příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Name`  
 Název čítače. Použít VSPerfCmd.exe **/querycounters** možnost Zobrazit jména dostupné čítače v počítači.  
  
 `Reload`  
 Počet událostí čítače v intervalu vzorkování. Nepoužívejte pomocí metody instrumentace.  
  
 `FriendlyName`  
 (Volitelné) Řetězec, který má použít místo `Name` v záhlaví sloupce sestavy profileru a zobrazení.  
  
## <a name="required-options"></a>Požadované možnosti  
 Možnost čítačů jde použít jenom s jedním z následujících možností:  
  
 **Spusťte:** `Trace`  
 Inicializuje možnost profileru pomocí metody instrumentace.  
  
 **Spuštění:** `AppName`  
 Spustí se zadanou aplikaci a profiler. Profiler musí být inicializovaný na použití metody vzorkování.  
  
 **Připojení:** `PID`  
 Spuštění profileru a připojí ho k proces zadaný pomocí ID procesu. Profiler musí být inicializovaný na použití metody vzorkování.  
  
## <a name="example"></a>Příklad  
 Ukázka metody vzorkování ukazuje, jak ukázková aplikace na každých 1000 výskyty NonHaltedCycles čítače obecný profileru.  
  
 Ukázka metody instrumentace ukazuje, jak inicializovat profileru začnete shromažďovat události L2InstructionFetches čítače. Název čítače L2InstructionFetches je specifické pro procesor.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)



