---
title: Úloha AssignTargetPath – | Microsoft Docs
description: Použijte úlohu MSBuild AssignTargetPath – k přijetí seznamu souborů a přidání atributů TargetPath, pokud již nejsou zadány.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f3a46b16bc689e0753b806c4239544e1ddbd73f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964937"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath – úloha

Tato úloha přijme seznam souborů a přidá atributy, `<TargetPath>` Pokud již nejsou zadány.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `AssignTargetPath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`RootFolder`|Volitelný `string` vstupní parametr.<br /><br /> Obsahuje cestu ke složce, která obsahuje cílové odkazy.|
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` vstupní parametr.<br /><br /> Obsahuje seznam příchozích souborů.|
|`AssignedFiles`|Volitelné<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`výstupní parametr<br /><br /> Obsahuje výsledný seznam souborů.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad spustí `AssignTargetPath` úlohu pro konfiguraci projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
