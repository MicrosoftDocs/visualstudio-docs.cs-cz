---
title: Úloha BscMake | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff0c95c37e24f8c51453a849159073baff8dca0d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593418"
---
# <a name="bscmake-task"></a>BscMake – úloha
> [!IMPORTANT]
> BscMake se už nepoužívá v integrovaném vývojovém prostředí sady Visual Studio. Od verze Visual Studio 2008 se informace o procházení ukládají automaticky do souboru *. sdf* ve složce *řešení* .

 Zabalí Nástroj pro údržbu informací o procházení Microsoftem (*BSCMAKE. exe*).  Nástroj *BSCMAKE. exe* vytvoří soubor s informacemi o procházení ( *. BSC*) ze zdrojových souborů prohlížeče ( *. sbr*), které se vytvoří během kompilace. K zobrazení souboru *. BSC* použijte **Prohlížeč objektů** . Další informace najdete v tématu [BSCMAKE reference](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy **BSCMAKE** . Většina parametrů úlohy odpovídá možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Například/\<možnost1 >/\<možnost2 >/\<možnost # >. Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **BSCMAKE** .<br /><br /> Další informace najdete v možnostech možností [BSCMAKE](/cpp/build/reference/bscmake-options).|
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru, který přepíše výchozí název výstupního souboru.<br /><br /> Další informace naleznete v možnosti **/o** v tématu [BSCMAKE Options](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, vynutí nepřírůstkové sestavení. Úplné, nepřírůstkové sestavení probíhá bez ohledu na to, zda soubor *. BSC* existuje a zabraňuje zkrácení souborů *. sbr* .<br /><br /> Další informace najdete v tématu věnovaném možnostem **/n** v tématu [Možnosti BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Prostředky**|Volitelný parametr **ITaskItem []** .<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v možnosti **/nologo** v tématu [BSCMAKE Options](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář pro protokol sledování.|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
