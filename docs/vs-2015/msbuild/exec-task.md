---
title: Úloha Exec | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a69fc64c3371a2970c03ec0129d4c733f5ae9cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201763"
---
# <a name="exec-task"></a>Exec – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spustí zadaný program nebo příkaz pomocí zadaných argumentů.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry pro `Exec` úlohu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Command`|Požadovaný parametr `String`.<br /><br /> Příkazy, které mají být spuštěny. Může se jednat o systémové příkazy, jako je například attrib nebo spustitelný soubor, například program.exe, runprogram.bat nebo setup.msi.<br /><br /> Tento parametr může obsahovat více řádků příkazů. Alternativně můžete do dávkového souboru vložit několik příkazů a spustit ho pomocí tohoto parametru.|  
|`CustomErrorRegularExpression`|Volitelný `String` parametr.<br /><br /> Určuje regulární výraz, který se používá k zaznamenání chybových řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytváří neobvykle formátovaný výstup.|  
|`CustomWarningRegularExpression`|Volitelný `String` parametr.<br /><br /> Určuje regulární výraz, který se používá k vypsání výstražných řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytváří neobvykle formátovaný výstup.|  
|`ExitCode`|Volitelný `Int32` výstup – parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytnut spuštěným příkazem.|  
|`IgnoreExitCode`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , úloha ignoruje ukončovací kód, který je poskytnut spuštěným příkazem. V opačném případě se úloha vrátí, `false` Pokud se spustí příkaz, který vrátí nenulový ukončovací kód.|  
|`IgnoreStandardErrorWarningFormat`|Volitelný `Boolean` parametr.<br /><br /> Pokud `false` se vybere řádky ve výstupu, které odpovídají standardnímu formátu chyb nebo upozornění, a zaprotokoluje je jako chyby nebo upozornění. `true`V takovém případě toto chování zakažte.|  
|`Outputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výstupní položky úkolu. `Exec`Tato úloha je nenastavuje. Místo toho je můžete zadat, jako by ji nastavili, aby bylo možné je použít později v projektu.|  
|`StdErrEncoding`|Volitelný `String` výstupní parametr.<br /><br /> Určuje kódování standardního streamu chyb zaznamenané úlohy. Výchozí hodnota je aktuální kódování výstupu konzoly.|  
|`StdOutEncoding`|Volitelný `String` výstupní parametr.<br /><br /> Určuje kódování standardního výstupního datového proudu zachycené úlohy. Výchozí hodnota je aktuální kódování výstupu konzoly.|  
|`WorkingDirectory`|Volitelný `String` parametr.<br /><br /> Určuje adresář, ve kterém se příkaz spustí.|  
  
## <a name="remarks"></a>Poznámky  
 Tato úloha je užitečná v případě [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , že konkrétní úloha pro úlohu, kterou chcete provést, není k dispozici. Tato úloha ale na `Exec` rozdíl od konkrétnější úlohy ale nemůže shromáždit výstup z nástroje nebo příkazu, který spouští.  
  
 `Exec`Úloha volá cmd.exe místo přímého vyvolání procesu.  
  
 Kromě parametrů uvedených v tomto dokumentu dědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Exec` úlohu ke spuštění příkazu.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
