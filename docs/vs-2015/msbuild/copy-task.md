---
title: Kopírovat úlohu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08442d6044ca978e69f199e76c4668db63c319da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196591"
---
# <a name="copy-task"></a>Copy – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zkopíruje soubory do nového umístění v systému souborů.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Copy` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`CopiedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky, které byly úspěšně zkopírovány.|  
|`DestinationFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam souborů, do kterého se mají kopírovat zdrojové soubory. Tento seznam by měl být se seznamem uvedeným v parametru `SourceFiles` v relaci 1 : 1. To znamená, že první soubor zadaný v části `SourceFiles` bude zkopírován na první místo zadané v části `DestinationFiles` a tak dále.|  
|`DestinationFolder`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje adresář, do kterého se mají soubory kopírovat. Musí se jednat o adresář, nikoli o soubor. Pokud adresář neexistuje, je automaticky vytvořen.|  
|`OverwriteReadOnlyFiles`|Volitelný `Boolean` parametr.<br /><br /> Přepsat soubory i v případě, že jsou označeny jako soubory určené pouze pro čtení|  
|`Retries`|Volitelný `Int32` parametr.<br /><br /> Určuje počet pokusů o kopírování, pokud se všechny předchozí pokusy nezdařily. Výchozím nastavením je nula.<br /><br /> **Poznámka:** Použití opakování může maskovat problém synchronizace v procesu sestavení.|  
|`RetryDelayMilliseconds`|Volitelný `Int32` parametr.<br /><br /> Určuje zpoždění mezi nezbytnými pokusy o opakování. Výchozí hodnotou je argument RetryDelayMillisecondsDefault, který je předán konstruktoru CopyTask.|  
|`SkipUnchangedFiles`|Volitelný `Boolean` parametr.<br /><br /> Je-li hodnota `true`, přeskočí se kopírování souborů, u kterých mezi zdrojem a cílem nedošlo ke změně. Úloha `Copy` považuje soubory za nezměněné, pokud mají stejnou velikost a je uveden stejný čas poslední aktualizace. **Poznámka:**  Pokud nastavíte tento parametr na `true` , neměli byste používat analýzu závislostí na nadřazeném cíli, protože tato úloha se spustí jenom v případě, že časy poslední změny zdrojových souborů jsou novější než časy poslední změny v cílových souborech.|  
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory ke kopírování.|  
|`UseHardlinksIfPossible`|Volitelný `Boolean` parametr.<br /><br /> Je-li hodnota `true`, pak namísto kopírování souborů vytvoří pevné odkazy na zkopírované soubory.|  
  
## <a name="warnings"></a>Upozornění  
 Jsou protokolována upozornění, včetně:  
  
- `Copy.DestinationIsDirectory`  
  
- `Copy.SourceIsDirectory`  
  
- `Copy.SourceFileNotFound`  
  
- `Copy.CreatesDirectory`  
  
- `Copy.HardLinkComment`  
  
- `Copy.RetryingAsFileCopy`  
  
- `Copy.FileComment`  
  
- `Copy.RemovingReadOnlyAttribute`  
  
## <a name="remarks"></a>Poznámky  
 Je nutné zadat buď parametr `DestinationFolder`, nebo `DestinationFiles`, nikoli však oba. Jsou-li zadány oba parametry, úloha se nezdaří a je zaznamenána chyba.  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad zkopíruje položky v kolekci položek `MySourceFiles` do složky c:\MyProject\Destination.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFolder="c:\MyProject\Destination"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje postup rekurzivního kopírování. Tento projekt rekurzivně zkopíruje všechny soubory z umístění c:\MySourceTree do umístění c:\MyDestinationTree a zachová strukturu adresářů.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
