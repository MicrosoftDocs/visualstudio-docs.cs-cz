---
title: XDCMake úkol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c41bfc2015f29cbb73b33df3594b3a3430af3f3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630649"
---
# <a name="xdcmake-task"></a>XDCMake – úloha

Zalomí nástroj dokumentace XML (*xdcmake.exe*), který sloučí soubory dokumentu XML (*.xdc)* do souboru *XML.*

 Soubor *XDC* je vytvořen při poskytování komentářů dokumentace ve zdrojovém kódu jazyka C++ a kompilace pomocí možnosti kompilátoru [/doc.](/cpp/build/reference/doc-process-documentation-comments-c-cpp) Další informace naleznete v [tématech XDCMake reference](/cpp/build/reference/xdcmake-reference), [XML Document Generator Tool stránky vlastností](/cpp/build/reference/xml-document-generator-tool-property-pages)a příkazový řádek nápovědy možnost (**/?**) pro *xdcmake.exe*.

## <a name="remarks"></a>Poznámky

 Ve výchozím nastavení podporuje nástroj *xdcmake.exe* několik možností příkazového řádku. Další možnosti jsou podporovány, pokud zadáte **/old** možnost příkazového řádku.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **XDCMake.**

|Parametr|Popis|
|---------------|-----------------|
|**Soubor additionaldocumentfile**|Volitelný **parametr String[].**<br /><br /> Určuje jeden nebo více dalších souborů *.xdc,* které mají být sloučeny.<br /><br /> Další informace naleznete v popisu **dalších souborů dokumentů** na [stránkách vlastností nástroje GENERÁTOR DOKUMENTŮ XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Viz také možnosti příkazového řádku **/old** a **/Fs** pro *soubor xdcmake.exe*.|
|**Další možnosti**|Volitelný **parametr String.**<br /><br /> Seznam možností určených na příkazovém řádku. Například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností, které nejsou reprezentovány žádným jiným parametrem úkolu **XDCMake.**<br /><br /> Další informace naleznete v [tématech XDCMake reference](/cpp/build/reference/xdcmake-reference), [XML Document Generator Tool stránky vlastností](/cpp/build/reference/xml-document-generator-tool-property-pages)a nápověda příkazového řádku (**/?**) pro *xdcmake.exe*.|
|**Závislosti knihovny dokumentů**|Volitelný **logický** parametr.<br /><br /> Pokud `true` a aktuální projekt má závislost na statické knihovny (*LIB*) projektu v řešení, soubory *.xDC* pro tento projekt knihovny jsou zahrnuty ve výstupu souboru *XML* pro aktuální projekt.<br /><br /> Další informace naleznete v popisu **závislostí knihovny dokumentů** na [stránkách vlastností nástroje Generátor dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**Výstupní soubor**|Volitelný **parametr String.**<br /><br /> Přepíše výchozí název výstupního souboru. Výchozí název je odvozen od názvu prvního souboru *.xdc,* který je zpracován.<br /><br /> Další informace naleznete v tématu **/out:\<filename>** option in [XDCMake reference](/cpp/build/reference/xdcmake-reference). Viz také možnosti příkazového řádku **/old** a **/Fo** pro *soubor xdcmake.exe*.|
|**Projectname**|Volitelný **parametr String.**<br /><br /> Název aktuálního projektu.|
|**LomítkoStaré**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, umožňuje další možnosti *xdcmake.exe.*<br /><br /> Další informace naleznete v parametru **/old** příkaz-line pro *soubor xdcmake.exe*.|
|**Zdrojů**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a vydávány úkoly.|
|**PotlačitStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu **/nologo** možnost v [XDCMake odkaz](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Volitelný **parametr String.**<br /><br /> Určuje adresář protokolu sledování.|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)