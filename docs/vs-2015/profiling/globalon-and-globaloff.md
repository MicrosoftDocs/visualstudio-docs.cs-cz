---
title: GlobalOn a GlobalOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae720bdd904c7b904c906022cea700512167617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434225"
---
# <a name="globalon-and-globaloff"></a>GlobalOn a GlobalOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnosti VSPerfCmd.exe **globaloff** a **GlobalOn** pozastaví a obnoví profilování pro všechny procesy a vlákna v relaci profilace z příkazového řádku.  
  
 Můžete zadat **GlobalOn** a **globaloff** jako jedinou možnost v příkazovém řádku VSPerfCmd.exe, nebo je můžete zahrnout do příkazových řádků, které také obsahují možnosti **Spustit**, **Spustit**nebo **připojit** .  
  
 **GlobalOn** a **globaloff** lze také kombinovat s možnostmi **ProcessOn**, **ProcessOff**, **ThreadOn**a **ThreadOff** .  
  
 Možnosti **GlobalOn** a **globaloff** pracují s možnostmi **ProcessOn** a **ProcessOff** , které řídí shromažďování dat pro zadaný proces, a s možnostmi **ThreadOn** a **ThreadOff** , které řídí shromažďování dat pro zadané vlákno.  
  
 Možnosti **globaloff** a **GlobalOn** mají vliv také na globální počet spuštění/zastavení, který je zpracován funkcemi rozhraní API profileru.  
  
- **Globaloff** hned nastaví globální počet spuštění/zastavení na hodnotu 0, a proto pozastaví profilaci.  
  
- **GlobalOn** hned nastaví globální počet spuštění/zastavení na 1, takže obnoví profilování.  
  
  Další informace najdete v tématu [rozhraní API pro nástroje pro profilaci](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="valid-options"></a>Platné možnosti  
 **GlobalOn** a **globaloff** lze zadat na příkazovém řádku, který obsahuje také následující možnosti.  
  
 **Začátek:**`Method`  
 Inicializuje relaci profileru příkazového řádku a nastaví určenou metodu profilace.  
  
 **Spustit:**`AppName`  
 Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.  
  
 **Připojit:**`PID`  
 Spustí profilování zadaného procesu.  
  
 {**ProcessOff**&#124;**ProcessOn**} **:**`PID`  
 Zastaví nebo spustí profilování pro zadaný proces.  
  
 {**ThreadOff**&#124;**ThreadOn**} **:**`TID`  
 Zastaví nebo spustí profilování pro zadaný proces (pouze metoda instrumentace).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používají možnosti **globaloff** a **GlobalOn** k tomu, abyste se vyhnuli shromažďování dat profilace pro spuštění a vypnutí aplikace.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
