---
title: Časovač | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 914b0c3e493e8486247704ef22967c8ccd511ed2
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50745000"
---
# <a name="timer"></a>Časovač
*VSPerfCmd.exe* **časovače** parametr nastaví události profilování, který se definuje tak, aby hodinových cyklů procesoru a volitelně změní počet cyklů v intervalu vzorkování z výchozí hodnoty 10 000 000. 10 000 000 hodinových cyklů procesoru s frekvencí 1 GHz (jeden GHz), je přibližně 100 vzorků za sekundu. Minimální počet cyklů, které je možné zadat je 50 000.  
  
 **Časovač** jde použít jenom při použití metoda profilování vzorkování a lze použít pouze v příkazovém řádku, který také obsahuje **spuštění** nebo **připojit** možnost.  
  
 Ve výchozím nastavení událost odběru vzorků profiler je nastavena na hodinových cyklů procesoru a interval vzorkování je nastavený na 10 000 000. **Časovače**, **PF**, **Sys**, a **čítač** možnosti umožňují nastavit událost odběru vzorků a interval odběru vzorků. **GC** možnost shromažďuje data paměti .NET v každé události přidělování a uvolňování paměti kolekce. Na příkazovém řádku lze zadat pouze jeden z těchto možností.  
  
 Událost odběru vzorků a interval vzorkování je možné nastavit pouze v první příkazového řádku, který obsahuje **spuštění** nebo **připojit** možnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Cycles`  
 Celočíselná hodnota, která určuje počet hodinových cyklů procesoru v intervalu vzorkování. Pokud `Cycles` není zadán, interval je nastavená na 10 000 000. Zadejte hodnotu bez čárkami.  
  
## <a name="required-options"></a>Požadované možnosti  
 **Časovač** lze zadat pouze na příkazovém řádku, který obsahuje jeden z následujících možností.  
  
 **Spuštění:** `AppName`  
 Spuštění profileru a aplikace určené `AppName`.  
  
 **Připojení:** `PID`  
 Připojí profiler pro proces určený identifikátorem procesu (`PID`).  
  
## <a name="invalid-options"></a>Neplatné možnosti  
 Tyto možnosti nelze zadat na stejném příkazovém řádku jako **časovače**.  
  
 **PF**[**:**`Events`]  
 Nastaví událost odběru vzorků na chyby stránek a volitelně nastaví interval vzorkování na `Events`. Výchozí interval PF je 10.  
  
 **Sys**[**:**`Events`]  
 Nastaví událost odběru vzorků na operační systém volá a volitelně nastaví interval vzorkování na `Events`. Výchozí Sys interval je 10.  
  
 **Čítač**[**:**`Name,Reload,FriendlyName`]  
 Nastaví událost odběru vzorků na výkon procesoru čítač určené `Name` a nastaví interval vzorkování na `Reload`.  
  
 **Uvolňování paměti**[**:**{**přidělení**&#124;**životnost**}]  
 Shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**), data se shromažďují v každé události přidělení paměti. Když **životnost** parametr zadán, data se shromažďují také na všechny události uvolňování paměti kolekce.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak nastavit interval vzorkování profileru na 1 000 000 cykly procesoru.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Viz také:  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)