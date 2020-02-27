---
title: Úloha GetFrameworkPath – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b907194c4818ff6b867e9d15b795506ef3b77476
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634003"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath – úloha

Načte cestu k sestavením .NET Framework.
Načte cestu k sestavením .NET Framework.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry úlohy `GetFrameworkPath`.

|Parametr|Popis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Volitelný výstupní parametr `String`.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 1,1, pokud je k dispozici. V opačném případě vrátí `null`.|
|`FrameworkVersion20Path`|Volitelný výstupní parametr `String`.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 2,0, pokud je k dispozici. V opačném případě vrátí `null`.|
|`FrameworkVersion30Path`|Volitelný výstupní parametr `String`.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,0, pokud je k dispozici. V opačném případě vrátí `null`.|
|`FrameworkVersion35Path`|Volitelný výstupní parametr `String`.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,5, pokud je k dispozici. V opačném případě vrátí `null`.|
|`FrameworkVersion40Path`|Volitelný výstupní parametr `String`.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 4,0, pokud je k dispozici. V opačném případě vrátí `null`.|
|`Path`|Volitelný výstupní parametr `String`.<br /><br /> Obsahuje cestu k nejnovějším sestavením rozhraní, pokud jsou k dispozici. V opačném případě vrátí `null`.|

## <a name="remarks"></a>Poznámky

Pokud je nainstalováno několik verzí .NET Framework, vrátí tato úloha verzi, na které je nástroj MSBuild navržený ke spuštění.

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá úlohu `GetFrameworkPath` k uložení cesty k .NET Framework ve vlastnosti `FrameworkPath`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
