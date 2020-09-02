---
title: Úloha BscMake | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed246255fc20b9660d24f234767fdeb451102f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684549"
---
# <a name="bscmake-task"></a>BscMake – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VÝZNAMNÁ
> BSCMAKE se už nepoužívá v integrovaném vývojovém prostředí sady Visual Studio. Od verze Visual Studio 2008 se informace o procházení ukládají automaticky do souboru. SDF ve složce řešení.  
  
 Zabalí Nástroj pro údržbu informací o procházení Microsoftem (bscmake.exe).  Nástroj bscmake.exe vytvoří soubor s informacemi o procházení (. BSC) ze zdrojových souborů prohlížeče (. SBR), které se vytvoří během kompilace. K zobrazení souboru. BSC použijte **Prohlížeč objektů** . Další informace najdete v tématu [BSCMAKE reference](https://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **BSCMAKE** . Většina parametrů úlohy odpovídá možnosti příkazového řádku.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností, jak je uvedeno na příkazovém řádku. Například "/*možnost1*  / *možnost2*  / *Option #*". Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **BSCMAKE** .<br /><br /> Další informace najdete v možnostech možností [BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru, který přepíše výchozí název výstupního souboru.<br /><br /> Další informace naleznete v možnosti **/o** v tématu [BSCMAKE Options](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Volitelný **logický** parametr.<br /><br /> Pokud `true` , vynutí nepřírůstkové sestavení. Úplné, nepřírůstkové sestavení probíhá bez ohledu na to, zda soubor. BSC existuje a zabraňuje zkrácení souborů. sbr.<br /><br /> Další informace najdete v tématu věnovaném možnostem **/n** v tématu [Možnosti BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**zdroje**|Volitelný parametr **ITaskItem []** .<br /><br /> Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.|  
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v možnosti **/nologo** v tématu [BSCMAKE Options](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář pro protokol sledování.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
