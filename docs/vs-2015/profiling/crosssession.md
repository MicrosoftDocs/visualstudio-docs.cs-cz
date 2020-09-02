---
title: CrossSession | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05e1f2360b3257e44fde1af8be3554dd7fd95115
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537174"
---
# <a name="crosssession"></a>CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost VSPerfCmd.exe **CrossSession** umožňuje profileru shromažďovat data z jakékoli relace konzoly. Možnost **CrossSession** je nutné použít s možností **Start** .  
  
 Místo **CrossSession**můžete použít zkratku **cs** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="valid-options"></a>Platné možnosti  
 Chcete-li povolit profilaci v jiné relaci, možnost **CrossSession** musí být zadána s možností **Start** . **CrossSession** se musí zadat taky v dalších příkazech připojení a **odpojení** **VSPerfCmd** .  
  
 **Začátek:**`Method`  
 Možnost **Spustit** inicializuje Profiler na určenou metodu profilace.  
  
 **Připojit:** _PID_[**,**_PID_]  
 Spustí profilování zadaných procesů.  
  
 **Detach**[**:**_PID_[;_PID_]]  
 Zastaví profilování zadaných procesů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá možnost **CrossSession** pro připojení k aplikaci, která byla spuštěna v jiné relaci konzoly.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
