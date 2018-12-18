---
title: Pro automatické označování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f63ee0e28a432e43f30377b9f876004b69cd13dc
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335730"
---
# <a name="automark"></a>AutoMark
**Pro automatické označování** možnost určuje počet milisekund, po mezi kolekce událostí čítače výkonu softwaru systému Windows. Čítače výkonu systému Windows jsou určené v **WinCounter** možnost.  
  
 Pouze jeden **pro automatické označování** možnost lze zadat na příkazovém řádku. Všimněte si, že **WinCounter** intervalu vzorkování určeného **pro automatické označování** je nezávislý na hlavní vzorkování intervalu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Parametry  
 `Milliseconds`  
 Určuje počet milisekund, po mezi kolekce událostí čítače výkonu systému Windows.  
  
## <a name="required-options"></a>Požadované možnosti  
 **WinCounter:** `Path`  
 Určuje čítačů výkonu systému Windows ke shromažďování. Při použití metody instrumentace, lze zadat více čítačů systému Windows. Při použití metody vzorkování, lze zadat pouze jeden čítač softwaru. **WinCounter** možnost je nutné zadat na příkazovém řádku, který obsahuje **spustit** možnost.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je interval vzorkování na 1000 milisekund nastavit pro dvě čítačů výkonu systému Windows.  
  
```cmd  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Viz také  
 [Vsperfcmd –](../profiling/vsperfcmd.md)   
 [Profil samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)