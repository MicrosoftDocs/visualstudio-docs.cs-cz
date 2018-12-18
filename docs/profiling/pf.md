---
title: PF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c86ce1c828ff3f090ce675aeed03a4911a55544
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258967"
---
# <a name="pf"></a>PF
*VSPerfCmd.exe* **PF** možnost nastavuje profilování událost, která je vzorků chyb stránek a volitelně změny počtu chyb stránek v intervalu vzorkování z výchozí hodnotu 10.  
  
> [!NOTE]
>  **PF** nelze použít na 64bitových systémech.  
  
**PF** lze použít pouze v příkazovém řádku, který také obsahuje **spusťte** nebo **Attach** možnost.  
  
 Ve výchozím nastavení událostí vzorkování nastavena na výkon procesoru Zastavit hodiny a interval vzorkování je nastaven na hodnotu 10 000 000. **Časovače**, **PF**, **Sys**, a **čítač** možnosti umožňují nastavit události a vzorkování intervalu vzorkování. **GC** možnost shromažďuje data paměti .NET v každé kolekci události přidělení a uvolňování paměti. Na příkazovém řádku lze zadat pouze jeden z těchto možností.  
  
 Vzorkování událostí a intervalu vzorkování lze nastavit pouze v první příkazového řádku, který obsahuje **spusťte** nebo **Attach** možnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Events`  
 Celočíselná hodnota, která určuje počet událostí selhání stránky v intervalu vzorkování. Pokud `Events` není zadán, interval je nastaven na hodnotu 10.  
  
## <a name="required-options"></a>Požadované možnosti  
 **PF** lze zadat pouze na příkazový řádek, který obsahuje jeden z následujících možností.  
  
 **Spusťte:** `AppName`  
 Spustí profileru a aplikace určeného AppName.  
  
 **Připojení:** `PID`  
 Připojí profileru k proces zadaný pomocí AppName.  
  
## <a name="invalid-options"></a>Neplatné možnosti  
 Nelze zadat následující možnosti na stejném příkazovém řádku jako **PF**.  
  
 **Časovač**[**:**`Cycles`]  
 Nastaví vzorkování události hodin procesoru cyklů a volitelně nastaví interval vzorkování na `Cycles`. Výchozí hodnota intervalu časovače je 10 000 000.  
  
 **Sys**[**:**`Events`]  
 Nastaví událostí vzorkování na volání z aplikace PROFILOVANÉHO s jádrem operačního systému (syscalls) a volitelně nastaví interval vzorkování na `Events`. Výchozí interval Sys je 10.  
  
 **Čítač:** `Name`[`,Reload`[`,FriendlyName`]]  
 Nastaví událostí vzorkování na výkon procesoru čítač určeného `Name` a nastaví interval vzorkování na `Reload`.  
  
 **Globální Katalog**[**:**{**přidělení**&#124;**životnost**}]  
 Shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**), data jsou shromažďována v každé události přidělení paměti. Když **životnost** je zadán parametr, data jsou shromažďována také v každé události kolekce paměti.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak nastavit profilování událost vzorku pro chyby stránky a nastavit interval vzorkování na 20 chyb stránek.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Viz také:  
 [Vsperfcmd –](../profiling/vsperfcmd.md)   
 [Profil samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)