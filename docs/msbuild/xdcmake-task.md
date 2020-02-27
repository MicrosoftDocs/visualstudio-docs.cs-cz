---
title: Úloha XDCMake | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630649"
---
# <a name="xdcmake-task"></a>XDCMake – úloha

Zabalí Nástroj dokumentace XML (*xdcmake. exe*), který sloučí soubory komentáře dokumentu XML ( *. xdc*) do souboru *. XML* .

 Soubor *. xdc* se vytvoří, když zadáte dokumentační komentáře ve C++ zdrojovém kódu a zkompilujete pomocí možnosti kompilátoru [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) . Další informace naleznete v tématu [Reference k xdcmake](/cpp/build/reference/xdcmake-reference), [stránky vlastností nástroje generátoru dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages)a možnost nápovědu příkazového řádku ( **/?** ) pro *xdcmake. exe*.

## <a name="remarks"></a>Poznámky

 Ve výchozím nastavení podporuje nástroj *xdcmake. exe* několik možností příkazového řádku. Další možnosti jsou podporovány při zadání možnosti příkazového řádku **/Old** .

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **xdcmake** .

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parametr volitelného **řetězce []** .<br /><br /> Určuje jeden nebo více dalších souborů *. xdc* ke sloučení.<br /><br /> Další informace najdete v popisu **dalších souborů dokumentů** v popisu na [stránkách vlastností nástroje generátoru dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Podívejte se také na možnosti příkazového řádku **/Old** a **/FS** pro *xdcmake. exe*.|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Například/\<možnost1 >/\<možnost2 >/\<možnost # >. Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **xdcmake** .<br /><br /> Další informace naleznete v tématu [Reference k xdcmake](/cpp/build/reference/xdcmake-reference), [stránky vlastností nástroje generátor dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages)a nápovědu příkazového řádku ( **/?** ) pro *xdcmake. exe*.|
|**DocumentLibraryDependencies**|Volitelný **logický** parametr.<br /><br /> Pokud `true` a aktuální projekt mají závislost na projektu statické knihovny ( *. lib*) v řešení, soubory *. xdc* pro tento projekt knihovny jsou zahrnuty ve výstupu souboru *. XML* pro aktuální projekt.<br /><br /> Další informace najdete v popisu **závislostí knihovny dokumentů** na [stránkách vlastností nástroje generátoru dokumentů XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Přepíše výchozí název výstupního souboru. Výchozí název je odvozen z názvu prvního souboru *. xdc* , který je zpracován.<br /><br /> Další informace naleznete v tématu možnost **/out:\<filename >** v tématu [xdcmake reference](/cpp/build/reference/xdcmake-reference). Podívejte se také na možnosti příkazového řádku **/Old** a **/FO** pro *xdcmake. exe*.|
|**Názevprojektu**|Volitelný **řetězcový** parametr.<br /><br /> Název aktuálního projektu|
|**SlashOld**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, povolí další možnosti *xdcmake. exe* .<br /><br /> Další informace naleznete v možnosti příkazového řádku **/Old** pro *xdcmake. exe*.|
|**Prostředky**|Vyžaduje se `ITaskItem[]` parametr.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu možnost **/nologo** v [xdcmake reference](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář pro protokol sledování.|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)