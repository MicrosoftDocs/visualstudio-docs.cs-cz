---
title: Argumenty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65759da4363891c713f906e6cb10f00443bcbceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197914"
---
# <a name="args"></a>Args
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost VSPerfCmd.exe **args** určuje seznam argumentů, které jsou předány cílové aplikaci **spouštěného** dílčího příkazu.  
  
 **Argumenty** lze použít pouze v případě, že je v příkazovém řádku uveden také příkaz **Spustit** . **Argumenty** jsou volitelné, pokud je zadán parametr **Launch** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Arguments`  
 Seznam argumentů cílové aplikace příkazu pro **spuštění** .  
  
## <a name="required-options"></a>Požadované možnosti  
 **Spustit:**`AppName`  
 Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá možnost **args** k předání argumentů TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
