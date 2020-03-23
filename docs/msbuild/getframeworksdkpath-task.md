---
title: Úloha cesty GetFrameworkSdkPath | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633990"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath – úloha

Načte cestu k sada Windows Software Development Kit (SDK).
## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `GetFrameworkSdkPath` úkolu.
Následující tabulka popisuje parametry `GetFrameworkSdkPath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k .NET SDK verze 2.0, pokud je k dispozici. V `String.Empty`opačném případě vrátí .|
|`FrameworkSdkVersion35Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k .NET SDK verze 3.5, pokud je k dispozici. V `String.Empty`opačném případě vrátí .|
|`FrameworkSdkVersion40Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k .NET SDK verze 4.0, pokud je k dispozici. V `String.Empty`opačném případě vrátí .|
|`Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k nejnovější .NET SDK, pokud je k dispozici libovolná verze. V `String.Empty`opačném případě vrátí .|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `GetFrameworkSdkPath` úlohu k uložení cesty k sadě Windows SDK ve vlastnosti. `SdkPath`

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
