---
title: Rozbalit úlohu | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3b02108e2ee47a31ced196643bf917b3b63c1c6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594900"
---
# <a name="unzip-task"></a>Rozbalit úlohu
Rozbalí archiv *zip* do zadaného umístění.

>[!NOTE]
>Úkol `Unzip` je k dispozici pouze v MSBuild 15,8 a vyšších.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `Unzip`.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFolder`|Povinný parametr <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Určuje cílovou složku, do které se má soubor rozbalit.|
|`OverwriteReadOnlyFiles`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, přepíše soubory jen pro čtení. Výchozí hodnota je `false`.|
|`SkipUnchangedFiles`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, přeskočí soubory rozzipovává, které se nezměnily. Výchozí hodnota je `true`. Úloha `Unzip` považuje soubory za nezměněné, pokud mají stejnou velikost a je uveden stejný čas poslední aktualizace.|
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje jeden nebo více souborů, které mají být extrahovány. Při zadávání více souborů, které jsou extrahovány, do stejné složky.|

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
 Následující příklad debalí archiv a přepíše všechny soubory jen pro čtení.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
