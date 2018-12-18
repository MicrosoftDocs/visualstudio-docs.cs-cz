---
title: ThreadOn a ThreadOff | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e908da955258bfef5d66187bc974b6e051a48ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789165"
---
# <a name="threadon-and-threadoff"></a>ThreadOn a ThreadOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **ThreadOff** a **ThreadOn** dílčí příkazy jsou dostupné jenom v příkazového řádku relace profilování, které používají metodu instrumentace. **ThreadOff** a **ThreadOn** pozastavit a obnovit profilace pro zadaný podproces. **ThreadOff** zastaví profilování vlákna a **ThreadOn** spuštění profilace vlákna.  
  
 Ve většině případů je zadat **ThreadOn** nebo **ThreadOff** jako jedinou možností v VSPerfCmd.exe příkazového řádku, ale můžete také kombinovat s **GlobalOn**, **GlobalOff**, **ProcessOn**, a **ProcessOff** dílčí příkazy.  
  
 **ThreadOn** a **ThreadOff** dílčí příkazy pracovat **GlobalOn** a **GlobalOff** dílčí příkazy, které řídí dat kolekce pro všechny procesy v relaci příkazového řádku profilování a **ProcessOn** a **ProcessOff** dílčí příkazy, které řídí shromažďování dat pro zadaný proces.  
  
 **ThreadOff** a **ThreadOn** dílčí příkazy také ovlivnit počet spuštění/zastavení vlákna, který je zpracováván pomocí funkcí profilování rozhraní API.  
  
- **ThreadOff** okamžitě počet operací spustit/zastavit vlákna nastaví na hodnotu 0 a proto pozastaví profilace.  
  
- **ThreadOn** okamžitě počet operací spustit/zastavit vlákna nastaví na 1 a proto obnoví profilace.  
  
  Další informace najdete v tématu [profilování rozhraní API nástroje](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `TID`  
 Celé číslo identifikátor vlákna spuštění nebo zastavení.  
  
## <a name="valid-options"></a>Platné možnosti  
 **ThreadOn** a **ThreadOff** se dá nastavit na příkazové řádky, které také obsahují následující dílčí příkazy.  
  
 **Spusťte:** `Method`  
 Inicializuje relaci příkazového řádku profilování a nastaví zadané metodě profilování.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Zastaví nebo spustí profilaci pro všechny procesy v relaci příkazového řádku profilování.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Zastavení nebo spuštění profilace pro zadaný proces.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu **ThreadOff** podpříkaz slouží k zastavení shromažďování dat profilování tak, aby se shromažďují pouze data po spuštění aplikace.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)



