---
title: Exec – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: f3d092a6d69f668ef48ca2f586494f848795c178
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300531"
---
# <a name="exec-task"></a>Exec – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Spustí zadaný program nebo příkaz pomocí zadaných argumentů.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Exec` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Command`|Vyžaduje `String` parametru.<br /><br /> Příkazy ke spuštění. Mohou to být systém příkazy, jako je například attrib, nebo spustitelný soubor, jako je například program.exe, runprogram.bat nebo setup.msi.<br /><br /> Tento parametr může obsahovat více řádků příkazů. Alternativně můžete umístit více příkazů v dávkovém souboru a spuštění s použitím tohoto parametru.|  
|`CustomErrorRegularExpression`|Volitelné `String` parametru.<br /><br /> Určuje regulární výraz, který se používá k přímé chyba vstupující výstup nástroje. To je užitečné pro nástroje, které neobvykle formátovaný výstup.|  
|`CustomWarningRegularExpression`|Volitelné `String` parametru.<br /><br /> Určuje regulární výraz, který se používá k přímé upozornění vstupující výstup nástroje. To je užitečné pro nástroje, které neobvykle formátovaný výstup.|  
|`ExitCode`|Volitelné `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytován provedeného příkazu.|  
|`IgnoreExitCode`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úkol bude ignorovat ukončovací kód, který je poskytován provedeného příkazu. V opačném případě úloha vrátí `false` provedeného příkazu vrátí nenulový ukončovací kód.|  
|`IgnoreStandardErrorWarningFormat`|Volitelné `Boolean` parametru.<br /><br /> Pokud `false`, vybere řádky ve výstupu, které odpovídají formátu Standardní chyby nebo upozornění a zaznamená jako chyby a upozornění. Pokud `true`, toto chování zakázat.|  
|`Outputs`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky výstup z úlohy. `Exec` Úloh tyto samotné nenastaví. Místo toho je lze je zadat jako, pokud nastavena, tak, aby bylo možné později v projektu.|  
|`StdErrEncoding`|Volitelné `String` výstupní parametr.<br /><br /> Určuje kódování standardní chybový proud zachycené úloh. Výchozí hodnota je aktuální kódování výstupu konzoly.|  
|`StdOutEncoding`|Volitelné `String` výstupní parametr.<br /><br /> Určuje kódování zachycené úloh standardního výstupního datového proudu. Výchozí hodnota je aktuální kódování výstupu konzoly.|  
|`WorkingDirectory`|Volitelné `String` parametru.<br /><br /> Určuje adresář, ve kterém se spustí příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 Tato úloha je užitečné, když konkrétní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úkolů pro úlohu, kterou chcete provést, není k dispozici. Ale `Exec` úkol, na rozdíl od více konkrétních úkolů nelze shromáždit výstup ze nástroj nebo příkaz, že běží.  
  
 `Exec` Úloh volá cmd.exe místo přímo vyvolání procesu.  
  
 Kromě uvedených v tomto dokumentu parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Exec` úkolů ke spuštění příkazu.  
  
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
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



