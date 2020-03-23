---
title: BscMake úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 668d42cdb0bc5cfb8dd344aab51ad0c66a838cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634510"
---
# <a name="bscmake-task"></a>Úkol BscMake

> [!IMPORTANT]
> BscMake již nepoužívá ide sady Visual Studio. Od aplikace Visual Studio 2008 je procházení informací automaticky uloženo v souboru *SDF* ve složce *Řešení.*

 Zabalí nástroj Microsoft Browse Information Maintenance Utility (*bscmake.exe*).  Nástroj *bscmake.exe* vytvoří informační soubor procházení (*bsc*) ze zdrojových souborů prohlížeče (*.sbr*), které jsou vytvořeny během kompilace. Pomocí **prohlížeče objektů** můžete zobrazit soubor *BSC.* Další informace naleznete v [tématu BSCMAKE reference](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **BscMake.** Většina parametrů úlohy odpovídá možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**Další možnosti**|Volitelný **parametr String.**<br /><br /> Seznam možností určených na příkazovém řádku. Například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností, které nejsou reprezentovány žádným jiným parametrem úkolu **BscMake.**<br /><br /> Další informace naleznete v možnostech v [možnostech BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Výstupní soubor**|Volitelný **parametr String.**<br /><br /> Určuje název souboru, který přepíše výchozí název výstupního souboru.<br /><br /> Další informace naleznete v tématu **/o** možnost v [BSCMAKE možnosti](/cpp/build/reference/bscmake-options).|
|**Zachovat SBR**|Volitelný **logický** parametr.<br /><br /> Pokud `true`vynutí nepřírůstkové sestavení. Úplné, nepřírůstkové sestavení dochází bez ohledu na to, zda existuje soubor *BSC* a zabraňuje zkrácení souborů *SBR.*<br /><br /> Další informace naleznete v tématu **/n** možnost v [BSCMAKE možnosti](/cpp/build/reference/bscmake-options).|
|**Zdrojů**|Volitelný parametr **ITaskItem[].**<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a vydávány úkoly.|
|**PotlačitStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu **/NOLOGO** možnost v [BSCMAKE možnosti](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Volitelný **parametr String.**<br /><br /> Určuje adresář protokolu sledování.|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
