---
title: Createitem – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a53bbac8f1d4549b49183d0e90b2f33c925654d6
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945297"
---
# <a name="createitem-task"></a>CreateItem – úloha
Naplní položku kolekce s vstupních položek. To umožňuje položky, které se mají zkopírovat z jednoho seznamu do jiného.  
  
> [!NOTE]
>  Tato úloha je zastaralý. Od verze rozhraní .NET Framework 3.5, položky skupiny může být umístěn v rámci [cílové](../msbuild/target-element-msbuild.md) elementy. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Atributy  
 Následující tabulka popisuje parametry `CreateItem` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AdditionalMetadata`|Volitelné `String` parametr pole.<br /><br /> Určuje další metadata se připojit k výstupní položky.  Zadejte název metadat a hodnotu pro položku s následující syntaxí:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Více dvojice název/hodnota metadat by měla být oddělena oddělte středníkem. Pokud název nebo hodnota obsahuje středníkem ani jiné speciální znaky, musejí být uvozeny. Další informace najdete v tématu [jak: řídicí speciální znaky v nástroji MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje položky, které chcete vyloučit z kolekce položek výstup. Tento parametr může obsahovat specifikaci zástupných znaků. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md) a [postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Vyžaduje <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametru.<br /><br /> Určuje položky, které chcete zahrnout do výstupu položku kolekce. Tento parametr může obsahovat specifikaci zástupných znaků.|  
|`PreserveExistingMetadata`|Volitelné `Boolean` parametru.<br /><br /> Pokud `True`, platí pouze pro další metadata již neexistují.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří novou kolekci položek s názvem `MySourceItemsWithMetadata` z kolekce položek `MySourceItems`. `CreateItem` Úloh naplní nové položky kolekce s položkami v `MySourceItems` položky. Potom přidá další metadata položku s názvem `MyMetadata` s hodnotou `Hello` na jednotlivé položky do nové kolekce.  
  
 Po spuštění úlohy `MySourceItemsWithMetadata` kolekce položek obsahuje položky *file1.resx* a *file2.resx*, s metadata položky pro `MyMetadata`. `MySourceItems` Zůstává stejná jako kolekce položek.  
  
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
  
 Následující tabulka popisuje výhody výstupní položku po spuštění úlohy. Metadata položky se zobrazí v závorkách po provedení položky.  
  
|Kolekce položek|Obsah|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|*File1.resx* (`MyMetadata="Hello"`)<br /><br /> *File2.resx* (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)