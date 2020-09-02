---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2bdb28f74dd305dc497521e95d38e00192c21c54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193606"
---
# <a name="gc-vsperfcmd"></a>Uvolňování paměti (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost **GC** umožňuje shromažďování .NET Framework přidělování paměti a dat o životnosti objektů. Možnost **GC** se dá použít jenom s metodou profilace vzorkování a jenom s možností **spuštění** .  
  
 Pokud používáte možnost **GC** , není příkaz VSPerfCLREnv **/sampleon** povinný.  
  
 Nejsou-li zadány žádné parametry nebo je-li zadán parametr **přidělení** , jsou shromažďována pouze .NET Framework data o přidělení paměti. Je-li zadán parametr **životnosti** , jsou shromažďována jak .NET Framework přidělování paměti, tak data o životnosti objektů .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Vyhrazen**  
 Default (Výchozí). Shromažďuje .NET Framework data o přidělování paměti.  
  
 **Doba platnosti**  
 Shromažďuje data přidělování .NET Framework paměti a data o životnosti objektů .NET Framework.  
  
## <a name="required-options"></a>Požadované možnosti  
 Možnost **GC** se dá použít jenom s možností **spuštění** .  
  
 **Spustit:**`AppName`  
 Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se spustí aplikace a shromáždí .NET Framework data o přidělování paměti.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
