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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf9c0df17ec0e1bb97c1426d5d312f616de0a8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747376"
---
# <a name="bscmake-task"></a>BscMake – úloha
> [!IMPORTANT]
> BscMake se už nepoužívá v integrovaném vývojovém prostředí sady Visual Studio. Od verze Visual Studio 2008 se informace o procházení ukládají automaticky do souboru *. sdf* ve složce *řešení* .

 Zabalí Nástroj pro údržbu informací o procházení Microsoftem (*BSCMAKE. exe*).  Nástroj *BSCMAKE. exe* vytvoří soubor s informacemi o procházení ( *. BSC*) ze zdrojových souborů prohlížeče ( *. sbr*), které se vytvoří během kompilace. K zobrazení souboru *. BSC* použijte **Prohlížeč objektů** . Další informace najdete v tématu [BSCMAKE reference](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy **BSCMAKE** . Většina parametrů úlohy odpovídá možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Například/\<option1 >/\<option2 >/\<option # >. Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **BSCMAKE** .<br /><br /> Další informace najdete v možnostech možností [BSCMAKE](/cpp/build/reference/bscmake-options).|
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru, který přepíše výchozí název výstupního souboru.<br /><br /> Další informace naleznete v možnosti **/o** v tématu [BSCMAKE Options](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, vynutí nepřírůstkové sestavení. Úplné, nepřírůstkové sestavení probíhá bez ohledu na to, zda soubor *. BSC* existuje a zabraňuje zkrácení souborů *. sbr* .<br /><br /> Další informace najdete v tématu věnovaném možnostem **/n** v tématu [Možnosti BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Prostředky**|Volitelný parametr **ITaskItem []** .<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v možnosti **/nologo** v tématu [BSCMAKE Options](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář pro protokol sledování.|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)