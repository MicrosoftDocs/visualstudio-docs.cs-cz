---
title: Označit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d7902ec588af2687b048639a930847ec02b3fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155784"
---
# <a name="mark"></a>Označení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost VSPerfCmd.exe **značka** vloží zadané informace do souboru dat profilování. Značka může být uvedena v samostatné sestavě VSPerfReport nebo v zobrazení zprávy pro uživatelské rozhraní profileru. **Značku** lze použít k určení počátečních a koncových bodů v filtrech sestav a zobrazení.  
  
 Možnost **Mark** musí být jedinou možností zadanou v příkazovém řádku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Uživatelsky definované celé číslo, které je uvedeno jako ID značky v zobrazeních a sestavách profileru. `MarkID` nemusí být jedinečný.  
  
 `MarkName`  
 Volitelné Uživatelem definovaný řetězec, který je uveden jako název značky v zobrazeních a sestavách profileru. Není `MarkName` -li parametr zadán, je pole název značky v seznamu značek prázdné. Uzavřete řetězce, které obsahují mezery nebo lomítka ("/") v uvozovkách.  
  
## <a name="example"></a>Příklad  
 Tento příklad vloží značku s ID 123 a názvem "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
