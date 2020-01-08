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
ms.openlocfilehash: 8fbe0dbda58a0c57cacd64c40b66cc640b779bca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593314"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath – úloha
Načte cestu k [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].

## <a name="task-parameters"></a>Parametry úlohy
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
Následující příklad používá úlohu `GetFrameworkSdkPath` k uložení cesty k [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ve vlastnosti `SdkPath`.

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

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
