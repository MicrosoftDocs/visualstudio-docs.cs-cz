---
title: LineOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbe8a715c5bb179c5293dd666f1879c07068d8b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583168"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení Profiler shromažďuje číslo řádku zdrojového kódu a čísla řádků posunu při použití metody profilace vzorkování. Možnost VSPerfCmd **LineOff** zakáže shromažďování dat pro číslo řádku, když se k spuštění aplikace VSPerfCmd používá. Data profilování se shromažďují na úrovni funkce, když je zadaný **LineOff** .  
  
 **LineOff** můžete použít jenom s možností **spuštění** a jenom v případě, že Profiler byl inicializován pro vzorkování pomocí možnosti **Start**:**Sample** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="required-options"></a>Požadované možnosti  
 Možnost **LineOff** lze použít pouze na příkazovém řádku, který obsahuje možnost **spuštění** .  
  
 **Spustit:**`AppName`  
 Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se spustí aplikace a Profiler a zakáže vzorkování na úrovni řádků.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
