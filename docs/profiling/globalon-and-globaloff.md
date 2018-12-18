---
title: GlobalOn a GlobalOff | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1731c47d3de9068affd4c7561e1dae94960b2b44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835914"
---
# <a name="globalon-and-globaloff"></a>GlobalOn a GlobalOff
*VSPerfCmd.exe* **GlobalOff** a **GlobalOn** možnosti pozastavení a pokračování profilování pro všechny procesy a vlákna v relaci příkazového řádku profilování.  
  
 Můžete zadat **GlobalOn** a **GlobalOff** jako možnosti pouze *VSPerfCmd.exe* příkazového řádku, nebo můžete zahrnout do příkazové řádky, které obsahují také  **Start**, **spuštění**, nebo **připojit** možnosti.  
  
 **GlobalOn** a **GlobalOff** se dají kombinovat taky s **ProcessOn**, **ProcessOff**, **ThreadOn**a  **ThreadOff** možnosti.  
  
 **GlobalOn** a **GlobalOff** možnosti pracovat **ProcessOn** a **ProcessOff** možnosti, které řídí shromažďování dat pro Zadaný proces a **ThreadOn** a **ThreadOff** možnosti, které řídí shromažďování dat pro zadaný podproces.  
  
 **GlobalOff** a **GlobalOn** možnosti také ovlivnit počet globální spuštění/zastavení, který je zpracováván funkcí rozhraní API profileru.  
  
- **GlobalOff** okamžitě Nastaví globální počet operací spustit/zastavit na hodnotu 0 a proto pozastaví profilace.  
  
- **GlobalOn** okamžitě Nastaví globální počet operací spustit/zastavit na hodnotu 1 a proto obnoví profilace.  
  
  Další informace najdete v tématu [nástroje rozhraní API pro profilaci](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="valid-options"></a>Platné možnosti  
 **GlobalOn** a **GlobalOff** se dá nastavit na příkazové řádky, které také obsahují následující možnosti.  
  
 **Spusťte:** `Method`  
 Inicializuje relaci příkazového řádku profileru a nastaví zadané metodě profilování.  
  
 **Spuštění:** `AppName`  
 Zadaná aplikace spustí a začne profilace pomocí metody odběru vzorků.  
  
 **Připojení:** `PID`  
 Zahájení profilace určeného procesu.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`PID`  
 Zastavení nebo spuštění profilace pro zadaný proces.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Zastavení nebo spuštění profilace pro zadaný proces (pouze metody instrumentace).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu **GlobalOff** a **GlobalOn** možnosti slouží k zamezení shromažďování profilovacích dat pro spuštění aplikace a vypnutí.  
  
```cmd  
; Initialize the profiler with profiling stopped.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff  
; Start an instrumented application and wait for it to warm up.  
; Start profiling.  
VSPerfCmd.exe /GlobalOn  
; Exercise the application functionality that you want to profile.  
; Stop profiling.  
VSPerfCmd.exe /GlobalOff  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Viz také:  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)