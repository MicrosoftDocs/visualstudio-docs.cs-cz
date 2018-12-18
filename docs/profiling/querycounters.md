---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f3c3176ea0b865ecf4a433a7a0a22a316720229
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257706"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** možnost uvádí čítače výkonu procesoru (hardware), které jsou k dispozici v počítači.  
  
 **QueryCounters** musí být pouze možnost na příkazovém řádku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="remarks"></a>Poznámky  
 Při použití metody instrumentace profileru může shromažďovat hodnoty jeden nebo více čítačů výkonu procesoru v každé události kolekce dat. Při použití metoda profilování se vzorkováním, můžete zadat jeden čítač událostí a počet výskytů události má být použit jako intervalu vzorkování.  
  
 Různé procesory zpřístupnit různé čítače výkonu procesoru. Profileru definuje sadu Obecné čítače, které lze použít na téměř všechny procesory. **QueryCounters** možnost uvádí názvy Obecné čítače i názvy čítačů, které jsou specifické pro procesor.  
  
## <a name="see-also"></a>Viz také:  
 [Vsperfcmd –](../profiling/vsperfcmd.md)   
 [Profil samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)