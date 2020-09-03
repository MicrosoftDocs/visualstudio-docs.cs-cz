---
title: QueryCounters | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdd2707a6af2b9d03e73c696884dc12413437b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178272"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost **QueryCounters** vypisuje čítače výkonu procesoru (hardware), které jsou k dispozici v počítači.  
  
 **QueryCounters** musí být jedinou možností na příkazovém řádku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="remarks"></a>Poznámky  
 Při použití metody instrumentace může Profiler shromažďovat hodnoty jednoho nebo více čítačů výkonu procesoru při každé události shromažďování dat. Při použití metody profilace vzorkování můžete zadat jednu událost čítače a počet výskytů událostí, které se mají použít jako interval vzorkování.  
  
 Různé procesory zveřejňují různé čítače výkonu procesoru. Profiler definuje sadu generických čítačů, které lze použít na téměř všech procesorech. Možnost **QueryCounters** vypisuje jak názvy obecných čítačů, tak názvy čítačů, které jsou specifické pro procesor.  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
