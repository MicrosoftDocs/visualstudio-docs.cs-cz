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
ms.openlocfilehash: ea44b7b98cce9bcb634217f504ea1f0529a2cf15
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298967"
---
# <a name="rc-task"></a>RC – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí nástroj Microsoft Windows Resource Compiler, RC. exe. Úloha **RC** kompiluje prostředky, jako jsou kurzory, ikony, bitmapy, dialogová okna a písma, do souboru prostředků (. res). Další informace naleznete v tématu "kompilátor prostředků" na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) .  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry RCtask. Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parametr volitelného **řetězce []** .<br /><br /> Přidá adresář do seznamu adresářů, ve kterých jsou vyhledávány soubory k zahrnutí.<br /><br /> Další informace naleznete v možnosti **/i** v tématu [použití RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN.|  
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností příkazového řádku, například **"** _/option1/option2/Option #_ ". Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy **RC** .<br /><br /> Další informace najdete v možnostech [použití RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN.|  
|**Jazykových**|Volitelný **řetězcový** parametr.<br /><br /> Určuje ID národního prostředí, které představuje jazykovou verzi použitou v prostředcích.<br /><br /> Další informace naleznete v části **/l** v tématu [použití RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN.|  
|**IgnoreStandardIncludePath**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, zabrání kompilátoru prostředků v kontrole souborů hlaviček nebo souborů prostředků v případě, že je vyhledává.<br /><br /> Další informace najdete v části **/x** v tématu [použití RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN.|  
|**NullTerminateStrings**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, hodnota null – ukončí všechny řetězce v tabulce řetězců.<br /><br /> Další informace najdete v tématu věnovaném použití RC na webu MSDN v možnosti **/n** [(příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) .|  
|**PreprocessorDefinitions**|Parametr volitelného **řetězce []** .<br /><br /> Zadejte jeden nebo více symbolů preprocesoru pro kompilátor prostředků. Zadejte seznam symbolů makra.<br /><br /> Další informace naleznete v tématu **/d** možnost použití verze [RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN. Viz také **UndefinePreprocessorDefinitions** v této tabulce.|  
|**ResourceOutputFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru prostředků. Zadejte název souboru prostředků.<br /><br /> Další informace naleznete v možnosti **/FO** v tématu [použití RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN.|  
|**ShowProgress**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, zobrazí zprávy, které vykazují průběh kompilátoru.<br /><br /> Další informace najdete v tématu možnost **/v** v tématu [použití RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN.|  
|**Zdrojová**|Vyžaduje se `ITaskItem[]` parametr.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|  
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace získáte zadáním **/?** . možnost příkazového řádku a potom se podívejte na možnost **/nologo** .|  
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář protokolu sledování.|  
|**UndefinePreprocessorDefinitions**|Zruší definici předprocesorového symbolu.<br /><br /> Další informace naleznete v části **/u** v tématu [použití RC (příkazový řádek RC)](https://go.microsoft.com/fwlink/?LinkId=155730) na webu MSDN. Viz také **PreprocessorDefinitions** v této tabulce.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
