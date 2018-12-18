---
title: RC – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0db327943dcaf9b14a921cf4437b6c23874b4380
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219429"
---
# <a name="rc-task"></a>RC – úloha
Zabalí nástroj Microsoft Windows Resource Compiler *rc.exe*. **RC** úloh zkompiluje prostředky, jako je například kurzorů, ikony, bitmapy, dialogová okna a písma, do prostředku (*.res*) soubor. Další informace najdete v tématu [Resource Compiler](https://docs.microsoft.com/windows/desktop/menurc/resource-compiler).
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úkolu RC. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Volitelné **String []** parametru.<br /><br /> Přidá adresář do seznamu adresáře, které se budou hledat vkládané soubory.<br /><br /> Další informace najdete v tématu **/I** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**AdditionalOptions**|Volitelné **řetězec** parametru.<br /><br /> Seznam možností příkazového řádku; třeba /\<možnost1 > /\<možnost2 > /\<možnost #>. Tento parametr použijte k určení možnosti příkazového řádku, které nejsou reprezentovány jakýkoli jiný **RC** parametr úlohy.<br /><br /> Další informace najdete v tématu Možnosti v [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**Jazyková verze**|Volitelné **řetězec** parametru.<br /><br /> Určuje ID národního prostředí, který představuje jazykovou verzi používané prostředky.<br /><br /> Další informace najdete v tématu **/l** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**IgnoreStandardIncludePath**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zabrání kontrole proměnná prostředí INCLUDE při hledání hlavičkové soubory nebo soubory prostředků kompilátor prostředků.<br /><br /> Další informace najdete v tématu **/x** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**NullTerminateStrings**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, všechny řetězce v tabulce řetězců končí hodnotou null.<br /><br /> Další informace najdete v tématu **/n** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**PreprocessorDefinitions**|Volitelné **String []** parametru.<br /><br /> Definujte symboly preprocesoru nejmíň jeden pro kompilátor prostředků. Zadejte seznam symboly maker.<br /><br /> Další informace najdete v tématu **/d** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730). Viz také **UndefinePreprocessorDefinitions** v této tabulce.|  
|**ResourceOutputFileName**|Volitelné **řetězec** parametru.<br /><br /> Určuje název souboru prostředků. Zadejte název souboru prostředku.<br /><br /> Další informace najdete v tématu **/fo** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**ShowProgress**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zobrazuje zprávy, které podávat zprávy o pokroku kompilátor.<br /><br /> Další informace najdete v tématu **/v** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**Zdroj**|Vyžaduje `ITaskItem[]` parametru.<br /><br /> Definuje pole objektů položky nástroje MSBuild zdrojových souborů, které lze používat a, protože ho vygeneroval úlohy.|  
|**SuppressStartupBanner**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.<br /><br /> Další informace získáte zadáním **/?** možnost příkazového řádku a přejděte **/nologo** možnost.|  
|**TrackerLogDirectory**|Volitelné **řetězec** parametru.<br /><br /> Určuje adresář protokolu sledovacího modulu.|  
|**UndefinePreprocessorDefinitions**|Definice preprocesoru symbolu.<br /><br /> Další informace najdete v tématu **/u** možnost [pomocí RC (RC příkazového řádku)](http://go.microsoft.com/fwlink/?LinkId=155730). Viz také **PreprocessorDefinitions** v této tabulce.|  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)