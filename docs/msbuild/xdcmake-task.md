---
title: Xdcmake – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 460d5f68242f232048fec294156f90f49331a21d
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231178"
---
# <a name="xdcmake-task"></a>XDCMake – úloha
Zabalí nástroj dokumentace XML (*xdcmake.exe*), která sloučí komentář k dokumentu XML (*.xdc*) soubory do *.xml* souboru.  
  
 *.Xdc* soubor je vytvořen při poskytování dokumentační komentáře ve zdrojovém kódu Visual C++ a kompilace pomocí [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) – možnost kompilátoru. Další informace najdete v tématu [referenční dokumentace nástroje XDCMake](/cpp/ide/xdcmake-reference), [stránky vlastností nástroje Generátor dokumentů XML](/cpp/ide/xml-document-generator-tool-property-pages)a možnost Nápověda příkazového řádku (**/?**) pro *xdcmake.exe* .  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení *xdcmake.exe* nástroj podporuje několik možností příkazového řádku. Další možnosti jsou podporované, když zadáte **/staré** možnost příkazového řádku.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **XDCMake** úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Volitelné **String []** parametru.<br /><br /> Určuje jeden nebo více dalších *.xdc* soubory ke sloučení.<br /><br /> Další informace najdete v tématu **další soubory dokumentu** popis v [stránky vlastností nástroje Generátor dokumentů XML](/cpp/ide/xml-document-generator-tool-property-pages). Viz také **/staré** a **/Fs** možnosti příkazového řádku pro *xdcmake.exe*.|  
|**AdditionalOptions**|Volitelné **řetězec** parametru.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Třeba /\<možnost1 > /\<možnost2 > /\<možnost #>. Tento parametr použijte k určení možností, které nejsou reprezentovány jakýkoli jiný **XDCMake** parametr úlohy.<br /><br /> Další informace najdete v tématu [referenční dokumentace nástroje XDCMake](/cpp/ide/xdcmake-reference), [stránky vlastností nástroje Generátor dokumentů XML](/cpp/ide/xml-document-generator-tool-property-pages)a Nápověda k příkazovému řádku (**/?**) pro *xdcmake.exe*.|  
|**DocumentLibraryDependencies**|Volitelné **logická** parametru.<br /><br /> Pokud `true` a aktuální projekt obsahuje závislost na statickou knihovnu (*lib*) projektu v řešení, *.xdc* jsou součástí souborů pro daný projekt knihovny *.xml* souboru výstupu pro aktuální projekt.<br /><br /> Další informace najdete v tématu **závislosti knihoven dokumentu** popis v [stránky vlastností nástroje Generátor dokumentů XML](/cpp/ide/xml-document-generator-tool-property-pages).|  
|**Výstupní soubor**|Volitelné **řetězec** parametru.<br /><br /> Přepíše výchozí název výstupního souboru. Výchozí název je odvozen z názvu prvního *.xdc* soubor, který je zpracován.<br /><br /> Další informace najdete v tématu **/out:\<název souboru >** možnost [referenční dokumentace nástroje XDCMake](/cpp/ide/xdcmake-reference). Viz také **/staré** a **/Fo** možnosti příkazového řádku pro *xdcmake.exe*.|  
|**ProjectName**|Volitelné **řetězec** parametru.<br /><br /> Název aktuálního projektu.|  
|**SlashOld**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, umožňuje další *xdcmake.exe* možnosti.<br /><br /> Další informace najdete v tématu **/staré** možnost příkazového řádku pro *xdcmake.exe*.|  
|**Zdroje**|Vyžaduje `ITaskItem[]` parametru.<br /><br /> Definuje pole objektů položky nástroje MSBuild zdrojových souborů, které lze používat a, protože ho vygeneroval úlohy.|  
|**SuppressStartupBanner**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.<br /><br /> Další informace najdete v tématu **/nologo** možnost [referenční dokumentace nástroje XDCMake](/cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Volitelné **řetězec** parametru.<br /><br /> Určuje adresář protokolu sledovacího modulu.|  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)