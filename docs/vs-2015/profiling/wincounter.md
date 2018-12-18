---
title: WinCounter | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a0e13869c46a9e2998252e819442bd61480b4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809275"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**WinCounter** určuje Windows nebo čítač výkonu aplikace na shromažďování v nastavených intervalech během profil spustit. Windows a čítače výkonu aplikace jsou uvedené jako značky v souboru dat profilování. Můžete zadat více čítačů výkonu k získání v samostatné možnosti.  
  
 Ve výchozím nastavení, se shromažďují čítače každých 500 milisekund. Použití **AutoMark** lze zadat interval jinou kolekci.  
  
 Pouze jeden **AutoMark** možnost se používá. Pokud je položek víc **AutoMark** možnosti se uvádějí, použije se ten poslední.  
  
 **WinCounter** možnost se dá použít jenom s **Start** možnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Path`  
 Čítače výkonu Windows ve formátu cesty čítače PDH.  
  
## <a name="required-options"></a>Požadované možnosti  
 **WinCounter** možnost se dá použít jenom s **Start** možnost.  
  
 **Spusťte:** `Method`  
 **Start** možnost inicializuje profiler k zadané metodě profilování.  
  
## <a name="exclusive-options"></a>Výhradní možnosti  
 **AutoMark** možnost se dá použít jenom s **WinCounter** možnost.  
  
 **AutoMark:** `Milliseconds`  
 Určuje počet milisekund mezi shromažďování dat čítačů výkonu Windows.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou uvedeny dva čítače výkonu Windows se mají shromažďovat v intervalu 1 000 milisekund.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)



