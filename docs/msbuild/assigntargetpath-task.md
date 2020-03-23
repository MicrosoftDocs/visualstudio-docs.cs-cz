---
title: Přiřadit úkol cílového cesty | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634536"
---
# <a name="assigntargetpath-task"></a>Přiřadit úkol TargetPath

Tato úloha přijme seznam souborů `<TargetPath>` a přidá atributy, pokud ještě nejsou zadány.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `AssignTargetPath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`RootFolder`|Volitelný `string` vstupní parametr.<br /><br /> Obsahuje cestu ke složce, která obsahuje cílové odkazy.|
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` vstupní parametr.<br /><br /> Obsahuje příchozí seznam souborů.|
|`AssignedFiles`|Nepovinné<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]` výstupního parametru.<br /><br /> Obsahuje výsledný seznam souborů.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad provede `AssignTargetPath` úlohu ke konfiguraci projektu.

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
