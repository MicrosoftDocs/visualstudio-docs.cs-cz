---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 981b37fe1ebaad5e45f0308143ab0384ef1d559b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145609"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost VSPerfCmd.exe **sys** nastaví událost profilování, která je Navzorkovaná na události systémového volání (volání funkcí z profilované aplikace do operačního systému), a volitelně změní počet systémových volání v intervalu vzorkování z výchozí hodnoty 10.  
  
 **Sys** se dá použít jenom v příkazovém řádku, který obsahuje taky možnost **Spustit** nebo **připojit** .  
  
 Ve výchozím nastavení je událost vzorkování profileru nastavená na taktové cykly procesoru a interval vzorkování je nastaven na 10 000 000. Možnosti **časovač**, **PF**, **sys**a **čítač** umožňují nastavit událost vzorkování a interval vzorkování. Možnost **GC** shromažďuje data paměti .NET při každé události přidělení a uvolňování paměti. V příkazovém řádku lze zadat pouze jednu z těchto možností.  
  
 Událost vzorkování a interval vzorkování lze nastavit pouze v prvním příkazovém řádku, který obsahuje možnost **Spustit** nebo **připojit** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Events`  
 Celočíselná hodnota, která určuje počet událostí systémových volání v intervalu vzorkování. Pokud `Events` parametr není zadán, je interval nastaven na hodnotu 10.  
  
## <a name="required-options"></a>Požadované možnosti  
 **Sys** vyžaduje jednu z následujících možností.  
  
 **Spustit:**`AppName`  
 Spustí Profiler a aplikaci určenou nástrojem `AppName` .  
  
 **Připojit:**`PID`  
 Připojí profiler k procesu určenému parametrem `PID` .  
  
## <a name="invalid-options"></a>Neplatné možnosti  
 Následující možnosti nelze zadat na stejném příkazovém řádku jako **sys**.  
  
 **PF**[**:** `Events` ]  
 Nastaví událost vzorkování na chyby stránkování a volitelně nastaví interval vzorkování na `Events` . Výchozí interval BF je 10.  
  
 **Časovač**[**:** `Cycles` ]  
 Nastaví událost vzorkování na časové cykly procesoru a volitelně nastaví interval vzorkování na `Cycles` . Výchozí interval časovače je 10 000 000.  
  
 **Čítač:** `Name` [`,Reload`[`,FriendlyName`]]  
 Nastaví událost vzorkování na čítač výkonu procesoru určený parametrem `Name` a nastaví interval vzorkování na `Reload` .  
  
 **GC**[**:**{**Allocation**&#124;**celoživotní**}]  
 Shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**) se data shromažďují při každé události přidělení paměti. Při zadání parametru **životnosti** se data shromažďují také při každé události uvolňování paměti.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak nastavit událost vzorkování profileru na systémová volání a jak nastavit interval vzorkování na 20 volání na vzorek.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
