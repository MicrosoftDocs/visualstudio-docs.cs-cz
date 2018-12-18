---
title: Označit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff40ac5db35927fad0fe28fe3c86c5411b5f5255
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769094"
---
# <a name="mark"></a>Označení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **označit** možnost vloží informace o zadaném do souboru dat profilování. Značky mohou být uvedeny v samostatných sestav VSPerfReport nebo v zobrazení sestav značky profilování uživatelského rozhraní. **Označit** slouží k určení počátečního a koncového bodu v filtry sestav a zobrazení.  
  
 **Označit** možnost musí být zadán v příkazovém řádku jedinou možností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Uživatelem definované číslo, které je uvedené jako ID značky v zobrazení profileru a sestavy. `MarkID` nemusí být jedinečný.  
  
 `MarkName`  
 (Volitelné) Uživatelem definovaný řetězec, který je uveden jako název značky v zobrazení profileru a sestavy. Pokud `MarkName` není zadán, pole název značky označit seznam je prázdný. Uzavření řetězců, které obsahují mezery nebo lomítka ("/") do uvozovek.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vloží značku s ID 123 a název značky "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)



