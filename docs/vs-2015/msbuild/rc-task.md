---
title: RC – úloha | Dokumentace Microsoftu
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
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04bd592f919ab3ced11b36dceba7ce4178927884
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259343"
---
# <a name="rc-task"></a>RC – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí nástroj Microsoft Windows Resource Compiler, rc.exe. **RC** úloh zkompiluje prostředky, jako je například kurzorů, ikony, bitmapy, dialogová okna a písma, do souboru prostředků (.res). Další informace najdete v tématu "Resource Compiler" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry RCtask. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Volitelné **String []** parametru.<br /><br /> Přidá adresář do seznamu adresáře, které se budou hledat vkládané soubory.<br /><br /> Další informace najdete v tématu **/I** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN.|  
|**AdditionalOptions**|Volitelné **řetězec** parametru.<br /><br /> Seznam příklad příkazového řádku optionsor **"**_/option1 /option2 /option#_". Tento parametr použijte k určení možnosti příkazového řádku, které nejsou reprezentovány jakýkoli jiný **RC** parametr úlohy.<br /><br /> Další informace najdete v tématu Možnosti v [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN.|  
|**Jazyková verze**|Volitelné **řetězec** parametru.<br /><br /> Určuje ID národního prostředí, který představuje jazykovou verzi používané prostředky.<br /><br /> Další informace najdete v tématu **/l** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN.|  
|**IgnoreStandardIncludePath**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zabrání kontrole proměnná prostředí INCLUDE při hledání hlavičkové soubory nebo soubory prostředků kompilátor prostředků.<br /><br /> Další informace najdete v tématu **/x** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN.|  
|**NullTerminateStrings**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, všechny řetězce v tabulce řetězců končí hodnotou null.<br /><br /> Další informace najdete v tématu **/n** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN.|  
|**PreprocessorDefinitions**|Volitelné **String []** parametru.<br /><br /> Definujte symboly preprocesoru nejmíň jeden pro kompilátor prostředků. Zadejte seznam symboly maker.<br /><br /> Další informace najdete v tématu **/d** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN. Viz také **UndefinePreprocessorDefinitions** v této tabulce.|  
|**ResourceOutputFileName**|Volitelné **řetězec** parametru.<br /><br /> Určuje název souboru prostředků. Zadejte název souboru prostředku.<br /><br /> Další informace najdete v tématu **/fo** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN.|  
|**ShowProgress**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zobrazuje zprávy, které podávat zprávy o pokroku kompilátor.<br /><br /> Další informace najdete v tématu **/v** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN.|  
|**Zdroj**|Vyžaduje `ITaskItem[]` parametru.<br /><br /> Definuje pole objektů položky nástroje MSBuild zdrojových souborů, které lze používat a, protože ho vygeneroval úlohy.|  
|**SuppressStartupBanner**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.<br /><br /> Další informace získáte zadáním **/?** možnost příkazového řádku a přejděte **/nologo** možnost.|  
|**TrackerLogDirectory**|Volitelné **řetězec** parametru.<br /><br /> Určuje adresář protokolu sledovacího modulu.|  
|**UndefinePreprocessorDefinitions**|Definice preprocesoru symbolu.<br /><br /> Další informace najdete v tématu **/u** možnost [pomocí RC (The RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730) na webové stránce MSDN. Viz také **PreprocessorDefinitions** v této tabulce.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



