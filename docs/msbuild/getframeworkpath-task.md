---
title: Úloha GetFrameworkPath – | Microsoft Docs
description: Naučte se, jak pomocí úlohy MSBuild GetFrameworkPath – načíst cestu k sestavením .NET Framework.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dea1b70335f7a1cc98bc1ee111ff58d69023c18a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914660"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath – úloha

Načte cestu k sestavením .NET Framework.
Načte cestu k sestavením .NET Framework.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `GetFrameworkPath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 1,1, pokud je k dispozici. Jinak vrací `null`.|
|`FrameworkVersion20Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 2,0, pokud je k dispozici. Jinak vrací `null`.|
|`FrameworkVersion30Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,0, pokud je k dispozici. Jinak vrací `null`.|
|`FrameworkVersion35Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,5, pokud je k dispozici. Jinak vrací `null`.|
|`FrameworkVersion40Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 4,0, pokud je k dispozici. Jinak vrací `null`.|
|`Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k nejnovějším sestavením rozhraní, pokud jsou k dispozici. Jinak vrací `null`.|

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
