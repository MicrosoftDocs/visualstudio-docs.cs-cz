---
title: Vypnutí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbbbd27cfe7d720349592050419f5c73d1843c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160230"
---
# <a name="shutdown"></a>Vypnutí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost **vypnutí** čeká na ukončení nebo odpojení jakéhokoli aktuálně profilované procesu a potom vypne Profiler a uzavře soubor dat profilování. Možnost **vypnutí** musí být posledním příkazem pro spuštění profilace.  
  
 Pokud není zadán parametr časového limitu, bude možnost **vypnutí** čekat na neomezenou dobu. Pokud je zadán parametr časového limitu, možnost se vrátí po zadaném počtu sekund, aniž by bylo nutné zapnout nebo zavřít Profiler nebo datový soubor.  
  
 Možnost **vypnutí** musí být jedinou možností zadanou v příkazovém řádku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parametry  
`Timeout`  
- Volitelné Když se tato možnost zadá, vrátí se po zadaném počtu sekund, aniž by se vypnul nebo zavřel soubor dat profilování.  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
