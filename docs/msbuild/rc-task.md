---
title: RC Úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 13ae844759cb73de6dc7bcce6c8898c21132f9d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632911"
---
# <a name="rc-task"></a>RC – úloha

Zalomí nástroj Kompilátor prostředků systému Microsoft Windows *rc.exe*. Úloha **RC** zkompiluje prostředky, jako jsou kurzory, ikony, bitmapy, dialogová okna a písma, do souboru prostředku (*.res).* Další informace naleznete v tématu [Resource Compiler](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy RC. Většina parametrů úlohy a několik sad parametrů odpovídají možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**Další includeředitelé adresáře**|Volitelný **parametr String[].**<br /><br /> Přidá adresář do seznamu adresářů, které jsou vyhledávány zahrnout soubory.<br /><br /> Další informace naleznete v tématu **/I** možnost [použití RC (rc příkazový řádek)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Další možnosti**|Volitelný **parametr String.**<br /><br /> Seznam možností příkazového řádku; například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností příkazového řádku, které nejsou reprezentovány žádným jiným parametrem úlohy **RC.**<br /><br /> Další informace naleznete v části [Použití rc (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Kultury**|Volitelný **parametr String.**<br /><br /> Určuje ID národního prostředí, které představuje jazykovou verzi používanou ve zdrojích.<br /><br /> Další informace naleznete v tématu **/l** možnost [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Ignorovat cestu standardních zahrnutí**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, zabrání kompilátoru prostředků v kontrole proměnné prostředí INCLUDE při hledání souborů hlaviček nebo souborů prostředků.<br /><br /> Další informace naleznete v tématu **/x** možnost [using RC (rc příkazový řádek)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Řetězce NullTerminateStrings**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, null ukončí všechny řetězce v tabulce řetězců.<br /><br /> Další informace naleznete v tématu **/n** možnost [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Definice preprocesoru**|Volitelný **parametr String[].**<br /><br /> Definujte jeden nebo více symbolů preprocesoru pro kompilátor prostředků. Zadejte seznam symbolů maker.<br /><br /> Další informace naleznete v tématu **/d** možnost [using RC (RC příkazový řádek)](/windows/win32/menurc/using-rc-the-rc-command-line-). Viz také **UndefinePreprocessorDefinitions** v této tabulce.|
|**ResourceOutputFileName**|Volitelný **parametr String.**<br /><br /> Určuje název souboru prostředků. Zadejte název souboru prostředků.<br /><br /> Další informace naleznete v tématu **/fo** option in [Using RC (the RC command line)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Zobrazit průběh**|Volitelný **logický** parametr.<br /><br /> Pokud `true`se zobrazí zprávy, které hlásí průběh kompilátoru.<br /><br /> Další informace naleznete v tématu **/v** možnost [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Zdroj**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a vydávány úkoly.|
|**PotlačitStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.<br /><br /> Další informace získáte zadáním pole **/?** příkazového řádku a pak se podívejte na možnost **/nologo.**|
|**TrackerLogDirectory**|Volitelný **parametr String.**<br /><br /> Určuje adresář protokolu sledování.|
|**UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions Undefine**|Zrušit definici symbolu preprocesoru.<br /><br /> Další informace naleznete v části **/u** v [části Použití RC (příkazový řádek RC).](/windows/win32/menurc/using-rc-the-rc-command-line-) Viz také **PreprocessorDefinitions** v této tabulce.|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)