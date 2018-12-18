---
title: Exec – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbefb90cad3b2aa3e6e7b0870548d44567ea8914
ms.sourcegitcommit: 56f3c31f1a06f6a6d2a8793b1abfa60cdf482497
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48817318"
---
# <a name="exec-task"></a>Exec – úloha
Spustí zadaný program nebo příkaz pomocí zadaných argumentů.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Exec` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Command`|Vyžaduje `String` parametru.<br /><br /> Příkazy ke spuštění. Může jít o systémové příkazy, jako je například attrib nebo spustitelný soubor, jako například *program.exe*, *runprogram.bat*, nebo *setup.msi*.<br /><br /> Tento parametr může obsahovat více řádků příkazů. Alternativně můžete umístit více příkazů v dávkovém souboru a spuštění s použitím tohoto parametru.|  
|`ConsoleOutput`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Každou výstupní položku je řádek ze standardního výstupu nebo standardního chybového proudu, protože ho vygeneroval nástroj. To se zachycuje, jenom Pokud `ConsoleToMsBuild` je nastavena na `true`.|
|`ConsoleToMsBuild`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha zaznamenají standardní chybu a standardní výstup nástroje a zpřístupnit je `ConsoleOutput` výstupní parametr.<br /><br />Výchozí hodnota: `false`.|  
|`CustomErrorRegularExpression`|Volitelné `String` parametru.<br /><br /> Určuje regulární výraz, který se používá k přímé chyba vstupující výstup nástroje. To je užitečné pro nástroje, které neobvykle formátovaný výstup.<br /><br />Výchozí hodnota: `null` (žádné vlastní zpracování).|  
|`CustomWarningRegularExpression`|Volitelné `String` parametru.<br /><br /> Určuje regulární výraz, který se používá k přímé upozornění vstupující výstup nástroje. To je užitečné pro nástroje, které neobvykle formátovaný výstup.<br /><br />Výchozí hodnota: `null` (žádné vlastní zpracování).|  
|`EchoOff`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha nebude generovat rozšířené formu `Command` protokolu MSBuild.<br /><br />Výchozí hodnota: `false`.|
|`ExitCode`|Volitelné `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytován provedeného příkazu.|  
|`IgnoreExitCode`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úkol bude ignorovat ukončovací kód, který je poskytován provedeného příkazu. V opačném případě úloha vrátí `false` provedeného příkazu vrátí nenulový ukončovací kód.<br /><br />Výchozí hodnota: `false`.|  
|`IgnoreStandardErrorWarningFormat`|Volitelné `Boolean` parametru.<br /><br /> Pokud `false`, vybere řádky ve výstupu, které odpovídají formátu Standardní chyby nebo upozornění a zaznamená jako chyby a upozornění. Pokud `true`, toto chování zakázat.<br /><br />Výchozí hodnota: `false`.|  
|`Outputs`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky výstup z úlohy. `Exec` Úloh tyto samotné nenastaví. Místo toho je lze je zadat jako, pokud nastavena, tak, aby bylo možné později v projektu.|  
|`StdErrEncoding`|Volitelné `String` výstupní parametr.<br /><br /> Určuje kódování standardní chybový proud zachycené úloh. Výchozí hodnota je aktuální kódování výstupu konzoly.|  
|`StdOutEncoding`|Volitelné `String` výstupní parametr.<br /><br /> Určuje kódování zachycené úloh standardního výstupního datového proudu. Výchozí hodnota je aktuální kódování výstupu konzoly.|  
|`WorkingDirectory`|Volitelné `String` parametru.<br /><br /> Určuje adresář, ve kterém se spustí příkaz.<br /><br />Výchozí: Aktuální pracovní adresáře projektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato úloha je užitečné, když konkrétní [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] úkolů pro úlohu, kterou chcete provést, není k dispozici. Ale `Exec` úkol, na rozdíl od více konkrétních úloh, nelze provést další zpracování nebo podmíněných operací na základě výsledku nástroje nebo příkaz, který běží.
  
 `Exec` Úkolů volání *cmd.exe* namísto vyvolání přímo procesu.  
  
 Kromě uvedených v tomto dokumentu parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Exec` úkolů ke spuštění příkazu.  
  
```xml  
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

## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
