---
title: Úloha XDCMake | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c16c92b41aa0635ecb24d83e30e2c347620b2c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675541"
---
# <a name="xdcmake-task"></a>XDCMake – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí Nástroj dokumentace XML (xdcmake.exe), který sloučí soubory komentáře dokumentu XML (. xdc) do souboru. XML.  
  
 Soubor. xdc se vytvoří, když zadáte dokumentační komentáře ve zdrojovém kódu Visual C++ a zkompilujete pomocí možnosti kompilátoru [/doc](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) . Další informace naleznete v tématu [Reference k xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [stránky vlastností nástroje generátoru dokumentů XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)a možnost Help příkazového řádku (**/?**) pro xdcmake.exe.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení nástroj xdcmake.exe podporuje několik možností příkazového řádku. Další možnosti jsou podporovány při zadání možnosti příkazového řádku **/Old** .  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **xdcmake** .  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Parametr volitelného **řetězce []** .<br /><br /> Určuje jeden nebo více dalších souborů. xdc ke sloučení.<br /><br /> Další informace najdete v popisu **dalších souborů dokumentů** v popisu na [stránkách vlastností nástroje generátoru dokumentů XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Viz také možnosti příkazového řádku **/Old** a **/FS** pro xdcmake.exe.|  
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Například "*/option1/option2/Option #*". Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **xdcmake** .<br /><br /> Další informace naleznete v tématu [Reference k xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [stránky vlastností nástroje generátor dokumentů XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)a nápovědu příkazového řádku (**/?**) pro xdcmake.exe.|  
|**DocumentLibraryDependencies**|Volitelný **logický** parametr.<br /><br /> Pokud `true` a aktuální projekt obsahuje závislost na projektu statické knihovny (. lib) v řešení, soubory. xdc pro tento projekt knihovny jsou zahrnuty ve výstupu souboru. XML pro aktuální projekt.<br /><br /> Další informace najdete v popisu **závislostí knihovny dokumentů** na [stránkách vlastností nástroje generátoru dokumentů XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Přepíše výchozí název výstupního souboru. Výchozí název je odvozen z názvu prvního souboru. xdc, který je zpracován.<br /><br /> Další informace najdete v referenčních informacích k **/out:** `filename` Option v [xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Přečtěte si také možnosti příkazového řádku **/Old** a **/FO** pro xdcmake.exe.|  
|**Názevprojektu**|Volitelný **řetězcový** parametr.<br /><br /> Název aktuálního projektu|  
|**SlashOld**|Volitelný **logický** parametr.<br /><br /> Pokud `true` povolíte další možnosti xdcmake.exe.<br /><br /> Další informace najdete v tématu **/Old** možnosti příkazového řádku pro xdcmake.exe.|  
|**zdroje**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|  
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu možnost **/nologo** v [xdcmake reference](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář pro protokol sledování.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
