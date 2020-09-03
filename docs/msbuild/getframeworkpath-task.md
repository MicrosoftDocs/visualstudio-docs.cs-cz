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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634003"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath – úloha

Načte cestu k sestavením .NET Framework.
Načte cestu k sestavením .NET Framework.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `GetFrameworkPath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 1,1, pokud je k dispozici. V opačném případě vrátí `null` .|
|`FrameworkVersion20Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 2,0, pokud je k dispozici. V opačném případě vrátí `null` .|
|`FrameworkVersion30Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,0, pokud je k dispozici. V opačném případě vrátí `null` .|
|`FrameworkVersion35Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,5, pokud je k dispozici. V opačném případě vrátí `null` .|
|`FrameworkVersion40Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 4,0, pokud je k dispozici. V opačném případě vrátí `null` .|
|`Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k nejnovějším sestavením rozhraní, pokud jsou k dispozici. V opačném případě vrátí `null` .|

## <a name="remarks"></a>Poznámky

Pokud je nainstalováno několik verzí .NET Framework, vrátí tato úloha verzi, na které je nástroj MSBuild navržený ke spuštění.

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `GetFrameworkPath` úlohu k uložení cesty k .NET Framework ve `FrameworkPath` Vlastnosti.

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
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
