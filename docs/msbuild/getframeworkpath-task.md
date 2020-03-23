---
title: Úloha getframeworkpath | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634003"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath – úloha

Načte cestu k sestavením rozhraní .NET Framework.
Načte cestu k sestavením rozhraní .NET Framework.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `GetFrameworkPath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavení rozhraní verze 1.1, pokud je k dispozici. V `null`opačném případě vrátí .|
|`FrameworkVersion20Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavení rozhraní verze 2.0, pokud je k dispozici. V `null`opačném případě vrátí .|
|`FrameworkVersion30Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavení rozhraní verze 3.0, pokud je k dispozici. V `null`opačném případě vrátí .|
|`FrameworkVersion35Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavení rozhraní verze 3.5, pokud je k dispozici. V `null`opačném případě vrátí .|
|`FrameworkVersion40Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavení rozhraní verze 4.0, pokud je k dispozici. V `null`opačném případě vrátí .|
|`Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k nejnovější sestavení rozhraní, pokud jsou k dispozici. V `null`opačném případě vrátí .|

## <a name="remarks"></a>Poznámky

Pokud je nainstalováno několik verzí rozhraní .NET Framework, vrátí tato úloha verzi, na které je msbuild určen ke spuštění.

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `GetFrameworkPath` úlohu k uložení cesty k `FrameworkPath` rozhraní .NET Framework ve vlastnosti.

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
