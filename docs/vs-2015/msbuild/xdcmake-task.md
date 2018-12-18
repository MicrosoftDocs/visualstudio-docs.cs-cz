---
title: Xdcmake – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: caf3803edff01e6ffe650f18aaccef99fc50728f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204877"
---
# <a name="xdcmake-task"></a>XDCMake – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí nástroj dokumentace XML (xdcmake.exe), která sloučí soubory komentáře (.xdc) dokumentu XML do souboru .xml.  
  
 Když zadáte dokumentační komentáře ve zdrojovém kódu Visual C++ a kompilace s využitím je vytvořen soubor .xdc [/doc](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) – možnost kompilátoru. Další informace najdete v tématu [referenční dokumentace nástroje XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [stránky vlastností nástroje Generátor dokumentů XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)a možnost Nápověda příkazového řádku (**/?**) pro xdcmake.exe.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení nástroj xdcmake.exe podporuje několik možností příkazového řádku. Další možnosti jsou podporované, když zadáte **/staré** možnost příkazového řádku.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **XDCMake** úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Volitelné **String []** parametru.<br /><br /> Určuje jeden nebo více souborů .xdc další ke sloučení.<br /><br /> Další informace najdete v tématu **další soubory dokumentu** popis v [stránky vlastností nástroje Generátor dokumentů XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Viz také **/staré** a **/Fs** možnosti příkazového řádku pro xdcmake.exe.|  
|**AdditionalOptions**|Volitelné **řetězec** parametru.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Například "*/option1 /option2 /option#*". Tento parametr použijte k určení možností, které nejsou reprezentovány jakýkoli jiný **XDCMake** parametr úlohy.<br /><br /> Další informace najdete v tématu [referenční dokumentace nástroje XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [stránky vlastností nástroje Generátor dokumentů XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)a Nápověda k příkazovému řádku (**/?**) pro xdcmake.exe.|  
|**DocumentLibraryDependencies**|Volitelné **logická** parametru.<br /><br /> Pokud `true` a aktuální projekt obsahuje závislost na statická knihovna (.lib) projektu v řešení, souborů .xdc pro daný projekt knihovny jsou součástí výstupu souboru .xml pro aktuální projekt.<br /><br /> Další informace najdete v tématu **závislosti knihoven dokumentu** popis v [stránky vlastností nástroje Generátor dokumentů XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**Výstupní soubor**|Volitelné **řetězec** parametru.<br /><br /> Přepíše výchozí název výstupního souboru. Výchozí název je odvozen z názvu prvního souboru .xdc, která je zpracována.<br /><br /> Další informace najdete v tématu **/out:** `filename` možnost [referenční dokumentace nástroje XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Viz také **/staré** a **/Fo** možnosti příkazového řádku pro xdcmake.exe.|  
|**ProjectName**|Volitelné **řetězec** parametru.<br /><br /> Název aktuálního projektu.|  
|**SlashOld**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, umožňuje xdcmake.exe Další možnosti.<br /><br /> Další informace najdete v tématu **/staré** možnost příkazového řádku pro xdcmake.exe.|  
|**Zdroje**|Vyžaduje `ITaskItem[]` parametru.<br /><br /> Definuje pole objektů položky nástroje MSBuild zdrojových souborů, které lze používat a, protože ho vygeneroval úlohy.|  
|**SuppressStartupBanner**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.<br /><br /> Další informace najdete v tématu **/nologo** možnost [referenční dokumentace nástroje XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|Volitelné **řetězec** parametru.<br /><br /> Určuje adresář protokolu sledovacího modulu.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



