---
title: Úloha XDCMake | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu XDCMake k zabalení nástroje dokumentace XML xdcmake.exe, který sloučí soubory komentářů dokumentu XML do souboru XML.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 62d1717acee9b8935f176bc10191f044b28a660d
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047276"
---
# <a name="xdcmake-task"></a>XDCMake – úloha

Zabalí Nástroj dokumentace XML ( *xdcmake.exe* ), který sloučí soubory komentáře dokumentu XML ( *. xdc* ) do souboru *. XML* .

 Soubor *. xdc* se vytvoří, když zadáte dokumentační komentáře ve zdrojovém kódu C++ a zkompilujete pomocí možnosti kompilátoru [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) . Další informace naleznete v tématu [Reference k xdcmake](/cpp/build/reference/xdcmake-reference), [stránky vlastností nástroje generátoru dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages)a možnost Help příkazového řádku ( **/?** ) pro *xdcmake.exe* .

## <a name="remarks"></a>Poznámky

 Ve výchozím nastavení nástroj *xdcmake.exe* podporuje několik možností příkazového řádku. Další možnosti jsou podporovány při zadání možnosti příkazového řádku **/Old** .

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **xdcmake** .

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parametr volitelného **řetězce []** .<br /><br /> Určuje jeden nebo více dalších souborů *. xdc* ke sloučení.<br /><br /> Další informace najdete v popisu **dalších souborů dokumentů** v popisu na [stránkách vlastností nástroje generátoru dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Viz také možnosti příkazového řádku **/Old** a **/FS** pro *xdcmake.exe* .|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Například/ \<option1>  / \<option2>  / \<option#> . Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **xdcmake** .<br /><br /> Další informace naleznete v tématu [Reference k xdcmake](/cpp/build/reference/xdcmake-reference), [stránky vlastností nástroje generátor dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages)a nápovědu příkazového řádku ( **/?** ) pro *xdcmake.exe* .|
|**DocumentLibraryDependencies**|Volitelný **logický** parametr.<br /><br /> Pokud `true` a aktuální projekt obsahuje závislost na projektu statické knihovny ( *. lib* ) v řešení, soubory *. xdc* pro tento projekt knihovny jsou zahrnuty ve výstupu souboru *. XML* pro aktuální projekt.<br /><br /> Další informace najdete v popisu **závislostí knihovny dokumentů** na [stránkách vlastností nástroje generátoru dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Přepíše výchozí název výstupního souboru. Výchozí název je odvozen z názvu prvního souboru *. xdc* , který je zpracován.<br /><br /> Další informace najdete v [referenčních](/cpp/build/reference/xdcmake-reference)informacích k **/out: \<filename>** Option v xdcmake. Přečtěte si také možnosti příkazového řádku **/Old** a **/FO** pro *xdcmake.exe* .|
|**Názevprojektu**|Volitelný **řetězcový** parametr.<br /><br /> Název aktuálního projektu|
|**SlashOld**|Volitelný **logický** parametr.<br /><br /> Pokud `true` povolíte další možnosti *xdcmake.exe* .<br /><br /> Další informace najdete v tématu **/Old** možnosti příkazového řádku pro *xdcmake.exe* .|
|**Prostředky**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu možnost **/nologo** v [xdcmake reference](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář pro protokol sledování.|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)