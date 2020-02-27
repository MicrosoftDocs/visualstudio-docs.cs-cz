---
title: Úloha AssignTargetPath – | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2d825c0c08ffeba1449954ed310644dd4437840
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634536"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath – – úloha

Tato úloha přijme seznam souborů a přidá atributy `<TargetPath>`, pokud již nejsou zadány.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry úlohy `AssignTargetPath`.

|Parametr|Popis|
|---------------|-----------------|
|`RootFolder`|Volitelný vstupní parametr `string`.<br /><br /> Obsahuje cestu ke složce, která obsahuje cílové odkazy.|
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>vstupní parametr `[]`.<br /><br /> Obsahuje seznam příchozích souborů.|
|`AssignedFiles`|Nepovinné<br /><br /> výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Obsahuje výsledný seznam souborů.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad spustí úlohu `AssignTargetPath` ke konfiguraci projektu.

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
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
