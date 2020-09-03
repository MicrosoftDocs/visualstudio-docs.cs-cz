---
title: Kopírovat úlohu | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fd0033f5ef6f83ca29432f95d6b635fcd36116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634367"
---
# <a name="copy-task"></a>Copy – úloha

Zkopíruje soubory do nového umístění v systému souborů.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Copy` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`CopiedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky, které byly úspěšně zkopírovány, *včetně* těch, které nebyly skutečně zkopírovány, ale byly přeskočeny, protože již byly aktuální a byly `SkipUnchangedFiles` `true` .|
|`DestinationFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam souborů, do kterého se mají kopírovat zdrojové soubory. Tento seznam by měl být se seznamem uvedeným v parametru `SourceFiles` v relaci 1 : 1. To znamená, že první soubor zadaný v části `SourceFiles` bude zkopírován na první místo zadané v části `DestinationFiles` a tak dále.|
|`DestinationFolder`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje adresář, do kterého se mají soubory kopírovat. Musí se jednat o adresář, nikoli o soubor. Pokud adresář neexistuje, je automaticky vytvořen.|
|`OverwriteReadOnlyFiles`|Volitelný `Boolean` parametr.<br /><br /> Přepsat soubory i v případě, že jsou označeny jako soubory určené pouze pro čtení|
|`Retries`|Volitelný `Int32` parametr.<br /><br /> Určuje počet pokusů o kopírování, pokud se všechny předchozí pokusy nezdařily. Výchozím nastavením je nula.<br /><br /> **Poznámka:** Použití opakování může maskovat problém synchronizace v procesu sestavení.|
|`RetryDelayMilliseconds`|Volitelný `Int32` parametr.<br /><br /> Určuje zpoždění mezi nezbytnými pokusy o opakování. Výchozí hodnotou je argument RetryDelayMillisecondsDefault, který je předán konstruktoru CopyTask.|
|`SkipUnchangedFiles`|Volitelný `Boolean` parametr.<br /><br /> Je-li hodnota `true`, přeskočí se kopírování souborů, u kterých mezi zdrojem a cílem nedošlo ke změně. Úloha `Copy` považuje soubory za nezměněné, pokud mají stejnou velikost a je uveden stejný čas poslední aktualizace. <br /><br /> **Poznámka:**  Pokud nastavíte tento parametr na `true` , neměli byste používat analýzu závislostí na nadřazeném cíli, protože tato úloha se spustí jenom v případě, že časy poslední změny zdrojových souborů jsou novější než časy poslední změny v cílových souborech.|
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

Následující příklad zkopíruje položky v `MySourceFiles` kolekci Item do složky *c:\MyProject\Destination*.

```xml
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

Následující příklad znázorňuje postup rekurzivního kopírování. Tento projekt kopíruje všechny soubory rekurzivně z *c:\MySourceTree* do *c:\MyDestinationTree*a přitom udržuje adresářovou strukturu.

```xml
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

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
