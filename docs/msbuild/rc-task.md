---
title: RC – úloha | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu RC k zabalení nástroje Microsoft Windows Resource Compiler, rc.exe, který kompiluje prostředky do souboru. res.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
- RC task (MSBuild (C++))
- MSBuild (C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a1babf518a3579246903f6479f999d8912dfe5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048789"
---
# <a name="rc-task"></a>RC – úloha

Zabalí nástroj Microsoft Windows Resource Compiler *rc.exe* . Úloha **RC** kompiluje prostředky, jako jsou kurzory, ikony, bitmapy, dialogová okna a písma, do souboru prostředků ( *. res* ). Další informace najdete v tématu [kompilátor prostředků](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úkolu RC. Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parametr volitelného **řetězce []** .<br /><br /> Přidá adresář do seznamu adresářů, ve kterých jsou vyhledávány soubory k zahrnutí.<br /><br /> Další informace naleznete v možnosti **/i** v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností příkazového řádku; například/ \<option1>  / \<option2>  / \<option#> . Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy **RC** .<br /><br /> Další informace najdete v možnostech [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Kultura**|Volitelný **řetězcový** parametr.<br /><br /> Určuje ID národního prostředí, které představuje jazykovou verzi použitou v prostředcích.<br /><br /> Další informace naleznete v části **/l** v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**IgnoreStandardIncludePath**|Volitelný **logický** parametr.<br /><br /> Pokud `true` , zabraňuje kompilátoru prostředků v kontrole souborů hlaviček nebo souborů prostředků v případě, že vyhledává soubory hlaviček.<br /><br /> Další informace najdete v části **/x** v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**NullTerminateStrings**|Volitelný **logický** parametr.<br /><br /> `true`V případě, že hodnota null – ukončí všechny řetězce v tabulce řetězců.<br /><br /> Další informace naleznete v části **/n** v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**PreprocessorDefinitions**|Parametr volitelného **řetězce []** .<br /><br /> Zadejte jeden nebo více symbolů preprocesoru pro kompilátor prostředků. Zadejte seznam symbolů makra.<br /><br /> Další informace naleznete v tématu **/d** možnost v [použití verze RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Viz také **UndefinePreprocessorDefinitions** v této tabulce.|
|**ResourceOutputFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru prostředků. Zadejte název souboru prostředků.<br /><br /> Další informace naleznete v možnosti **/FO** v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**ShowProgress**|Volitelný **logický** parametr.<br /><br /> Pokud `true` se zobrazí zprávy, které vykazují průběh kompilátoru.<br /><br /> Další informace naleznete v možnosti **/v** v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Zdroj**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace získáte zadáním **/?** . možnost příkazového řádku a potom se podívejte na možnost **/nologo** .|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář protokolu sledování.|
|**UndefinePreprocessorDefinitions**|Zruší definici předprocesorového symbolu.<br /><br /> Další informace naleznete v možnosti **/u** v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Viz také **PreprocessorDefinitions** v této tabulce.|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)