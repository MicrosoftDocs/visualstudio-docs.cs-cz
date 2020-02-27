---
title: Úloha GetFrameworkSdkPath – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021bdb485846749ea2c7e9dfe483e09738fda46
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633990"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath – úloha

Načte cestu k sadě Windows Software Development Kit (SDK).
## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry úlohy `GetFrameworkSdkPath`.
Následující tabulka popisuje parametry úlohy `GetFrameworkSdkPath`.

|Parametr|Popis|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k sadě .NET SDK verze 2,0, pokud je k dispozici. V opačném případě vrátí `String.Empty`.|
|`FrameworkSdkVersion35Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k sadě .NET SDK verze 3,5, pokud je k dispozici. V opačném případě vrátí `String.Empty`.|
|`FrameworkSdkVersion40Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k sadě .NET SDK verze 4,0, pokud je k dispozici. V opačném případě vrátí `String.Empty`.|
|`Path`|Volitelný výstupní parametr `String`.<br /><br /> Obsahuje cestu k nejnovější sadě .NET SDK, pokud je k dispozici nějaká verze. V opačném případě vrátí `String.Empty`.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá úlohu `GetFrameworkSdkPath` k uložení cesty k Windows SDK ve vlastnosti `SdkPath`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
