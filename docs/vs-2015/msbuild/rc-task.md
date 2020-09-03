---
title: RC – úloha | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81f64ec9774410ea55897445836c8633fe98e7bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851734"
---
# <a name="rc-task"></a>RC – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí nástroj Microsoft Windows Resource Compiler rc.exe. Úloha **RC** kompiluje prostředky, jako jsou kurzory, ikony, bitmapy, dialogová okna a písma, do souboru prostředků (. res). Další informace naleznete v tématu "kompilátor prostředků" na webu [MSDN](https://msdn.microsoft.com/) .  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry RCtask. Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parametr volitelného **řetězce []** .<br /><br /> Přidá adresář do seznamu adresářů, ve kterých jsou vyhledávány soubory k zahrnutí.<br /><br /> Další informace naleznete v možnosti **/i** v tématu [použití RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN.|  
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností příkazového řádku, například **"**_/option1/option2/Option #_". Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy **RC** .<br /><br /> Další informace najdete v možnostech [použití RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN.|  
|**Kultura**|Volitelný **řetězcový** parametr.<br /><br /> Určuje ID národního prostředí, které představuje jazykovou verzi použitou v prostředcích.<br /><br /> Další informace naleznete v části **/l** v tématu [použití RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN.|  
|**IgnoreStandardIncludePath**|Volitelný **logický** parametr.<br /><br /> Pokud `true` , zabraňuje kompilátoru prostředků v kontrole souborů hlaviček nebo souborů prostředků v případě, že vyhledává soubory hlaviček.<br /><br /> Další informace najdete v části **/x** v tématu [použití RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN.|  
|**NullTerminateStrings**|Volitelný **logický** parametr.<br /><br /> `true`V případě, že hodnota null – ukončí všechny řetězce v tabulce řetězců.<br /><br /> Další informace najdete v tématu věnovaném použití RC na webu MSDN v možnosti **/n** [(příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) .|  
|**PreprocessorDefinitions**|Parametr volitelného **řetězce []** .<br /><br /> Zadejte jeden nebo více symbolů preprocesoru pro kompilátor prostředků. Zadejte seznam symbolů makra.<br /><br /> Další informace naleznete v tématu **/d** možnost použití verze [RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN. Viz také **UndefinePreprocessorDefinitions** v této tabulce.|  
|**ResourceOutputFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru prostředků. Zadejte název souboru prostředků.<br /><br /> Další informace naleznete v možnosti **/FO** v tématu [použití RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN.|  
|**ShowProgress**|Volitelný **logický** parametr.<br /><br /> Pokud `true` se zobrazí zprávy, které vykazují průběh kompilátoru.<br /><br /> Další informace najdete v tématu možnost **/v** v tématu [použití RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN.|  
|**Zdroj**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|  
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace získáte zadáním **/?** . možnost příkazového řádku a potom se podívejte na možnost **/nologo** .|  
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář protokolu sledování.|  
|**UndefinePreprocessorDefinitions**|Zruší definici předprocesorového symbolu.<br /><br /> Další informace naleznete v části **/u** v tématu [použití RC (příkazový řádek RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) na webu MSDN. Viz také **PreprocessorDefinitions** v této tabulce.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
