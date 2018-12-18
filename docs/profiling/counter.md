---
title: Čítač | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bfc59eb1cec7e4ed5ef9b7955438fffb03ca5d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832898"
---
# <a name="counter"></a>Čítač
**Čítač** možnost shromažďuje data z čítače výkonu procesoru (hardwaru).  
  
- Při použití metoda profilování vzorkování **čítač** určuje čítač výkonu na čipu a počet událostí čítače pro použití jako interval vzorkování. Při použití vzorkování, můžete zadat pouze jeden čítač.  
  
- Při použití metoda profilace instrumentace, číslo události čítače, ke kterým došlo v intervalu mezi událostmi předchozích a aktuálních kolekce jsou uvedené jako samostatná pole v sestavách profileru. Více **čítač** možnosti lze zadat, pokud používáte instrumentace.  
  
  Každý typ procesoru má svou vlastní sadu čítačů výkonu hardwaru. Profiler definuje sadu čítačů obecný výkonu, které jsou společné pro téměř všechny procesory. Chcete-li seznam čítačů obecný a specifické pro procesor v počítači, použijte příkazu vsperfcmd proveďte **QueryCounters** příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```cmd  
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
  
```cmd  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Viz také:  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)