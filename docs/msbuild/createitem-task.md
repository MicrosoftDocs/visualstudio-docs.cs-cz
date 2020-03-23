---
title: Úkol Vytvořit položku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4364e6c3f637fdf2c3e02a52d3163e5cdd8a5861
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634328"
---
# <a name="createitem-task"></a>CreateItem – úloha

Naplní kolekce položek vstupními položkami. To umožňuje zkopírovat položky z jednoho seznamu do druhého.

> [!NOTE]
> Tento úkol je zastaralé. Počínaje rozhraním .NET Framework 3.5 mohou být skupiny položek umístěny v rámci [cílových](../msbuild/target-element-msbuild.md) prvků. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

## <a name="attributes"></a>Atributy

 Následující tabulka popisuje parametry `CreateItem` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AdditionalMetadata`|Volitelný `String` parametr pole.<br /><br /> Určuje další metadata, která se mají připojit k výstupním položkám.  Zadejte název metadat a hodnotu položky s následující syntaxí:<br /><br /> *Hodnota* `=` metadat název *metadat*<br /><br /> Více párů názvů a hodnot metadat by mělo být odděleno středníkem. Pokud název nebo hodnota obsahuje středník nebo jiné speciální znaky, musí být uvozeny. Další informace naleznete [v tématu How to: Escape special characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|
|`Exclude`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje položky, které mají být vyloučeny z kolekce výstupních položek. Tento parametr může obsahovat specifikace zástupných symbolů. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md) and [How to: Exclude files from the build](../msbuild/how-to-exclude-files-from-the-build.md).|
|`Include`|Povinný <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametr.<br /><br /> Určuje položky, které mají být zahrnuty do kolekce výstupních položek. Tento parametr může obsahovat specifikace zástupných symbolů.|
|`PreserveExistingMetadata`|Volitelný `Boolean` parametr.<br /><br /> Pokud `True`platí pouze další metadata, pokud ještě neexistují.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad kódu vytvoří novou `MySourceItemsWithMetadata` kolekci položek `MySourceItems`pojmenovanou z kolekce položek . Úkol `CreateItem` naplní novou kolekci položek v `MySourceItems` položce. Potom přidá další položku `MyMetadata` metadat s `Hello` názvem s hodnotou každé položky v nové kolekci.

 Po provedení úlohy obsahuje `MySourceItemsWithMetadata` kolekce položek položky *file1.resx* a *file2.resx*, `MyMetadata`obě s položkami metadat pro . Kolekce `MySourceItems` položek se nezmění.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceItems Include="file1.resx;file2.resx" />
    </ItemGroup>

    <Target Name="NewItems">
        <CreateItem
            Include="@(MySourceItems)"
            AdditionalMetadata="MyMetadata=Hello">
           <Output
               TaskParameter="Include"
               ItemName="MySourceItemsWithMetadata"/>
        </CreateItem>

    </Target>

</Project>
```

 Následující tabulka popisuje hodnotu výstupní položky po provedení úlohy. Metadata položky jsou zobrazena v závorce za položkou.

|Kolekce položek|Obsah|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*soubor1.resx* `MyMetadata="Hello"`( )<br /><br /> *soubor2.resx* `MyMetadata="Hello"`( )|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
