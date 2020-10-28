---
title: Úloha CreateItem – | Microsoft Docs
description: Pomocí úlohy MSBuild CreateItem – můžete naplnit kolekce položek vstupními položkami a umožnit tak kopírování položek z jednoho seznamu do jiného.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ed964c618b59bf02086329715c5b0540039eb16a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796755"
---
# <a name="createitem-task"></a>CreateItem – úloha

Naplní kolekce položek vstupními položkami. To umožňuje kopírování položek z jednoho seznamu do jiného.

> [!NOTE]
> Tato úloha je zastaralá. Počínaje .NET Framework 3,5 mohou být skupiny položek umístěny v rámci [cílových](../msbuild/target-element-msbuild.md) elementů. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="attributes"></a>Atributy

 Následující tabulka popisuje parametry `CreateItem` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AdditionalMetadata`|Volitelný `String` parametr pole.<br /><br /> Určuje další metadata, která se mají připojit k výstupním položkám.  Zadejte název a hodnotu metadat pro položku s následující syntaxí:<br /><br /> *Metadata* `=` *MetadataValue*<br /><br /> Páry názvů a hodnot s více metadaty by měly být odděleny středníkem. Pokud název nebo hodnota obsahují středník nebo jiné speciální znaky, musí být uvozeny řídicími znaky. Další informace naleznete v tématu [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|
|`Exclude`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje položky, které mají být vyloučeny z kolekce výstupních položek. Tento parametr může obsahovat specifikace zástupných znaků. Další informace naleznete v tématu [položky](../msbuild/msbuild-items.md) a [Postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).|
|`Include`|Povinný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, které se mají zahrnout do kolekce výstupních položek. Tento parametr může obsahovat specifikace zástupných znaků.|
|`PreserveExistingMetadata`|Volitelný `Boolean` parametr.<br /><br /> Pokud `True` , použijte další metadata pouze v případě, že ještě neexistují.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad kódu vytvoří novou kolekci položek s názvem `MySourceItemsWithMetadata` z kolekce Items `MySourceItems` . `CreateItem`Úkol naplní novou kolekci položek položkami v `MySourceItems` položce. Pak přidá další položku metadat s názvem `MyMetadata` s hodnotou `Hello` pro každou položku v nové kolekci.

 Po spuštění úlohy `MySourceItemsWithMetadata` kolekce položek obsahuje položky *Soubor1. resx* a *Soubor2. resx* s položkami metadat pro `MyMetadata` . `MySourceItems`Kolekce položek se nezměnila.

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

 Následující tabulka popisuje hodnotu výstupní položky po provedení úkolu. Metadata položky se zobrazí v závorkách za položkou.

|Kolekce položek|Obsah|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*Soubor1. resx* ( `MyMetadata="Hello"` )<br /><br /> *Soubor2. resx* ( `MyMetadata="Hello"` )|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
