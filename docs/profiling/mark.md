---
title: Označit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89a26a3a3729241cb4ec9180e6cb16f131194b86
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844791"
---
# <a name="mark"></a>Označení
*VSPerfCmd.exe* **označit** možnost vloží informace o zadaném do profilování datového souboru. Označit může být uvedený v samostatných vsperfreport – sestavy nebo v zobrazení sestavy označit profilování uživatelského rozhraní. **Označit** dá použít k zadání počátečního a koncového bodu v sestavu a zobrazte filtry.  
  
 **Označit** možnost musí být pouze možnost zadat na příkazovém řádku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Číslo definovaný uživatelem, které je uveden jako ID značky v zobrazení profileru a sestavy. `MarkID` nemá být jedinečný.  
  
 `MarkName`  
 (Volitelné) Řetězec definovaný uživatelem, který je uveden jako název značky v zobrazení profileru a sestavy. Pokud `MarkName` není zadán název značky pole výpis označit je prázdný. Uzavřete řetězce, které obsahují mezery nebo předávat lomítka ("/") v uvozovkách.  
  
## <a name="example"></a>Příklad  
 Tento příklad vloží značku s ID 123 a název značky "TestMark".  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Viz také:  
 [Vsperfcmd –](../profiling/vsperfcmd.md)   
 [Profil samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)