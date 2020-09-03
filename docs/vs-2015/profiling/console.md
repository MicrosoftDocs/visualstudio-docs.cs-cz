---
title: Konzola | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e947fb28c92323f0d4d66c697c272699fc63450e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161310"
---
# <a name="console"></a>Konzola
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost **konzoly** VSPerfCmd.exe spustí zadanou aplikaci v novém okně příkazového řádku. **Konzolu** lze použít pouze s možností **spuštění** VSPerfCmd. Pokud aplikace není aplikace příkazového řádku, **Konzola** nemá žádný vliv.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="required-options"></a>Požadované možnosti  
 **Konzolu** lze zadat pouze v příkazovém řádku, který obsahuje také možnost **spuštění** .  
  
 **Spustit:**`AppName`  
 Spustí Profiler a aplikaci určenou nástrojem `AppName` .  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
