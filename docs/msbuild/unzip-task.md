---
title: Rozbalit úlohu | Microsoft Docs
description: Přečtěte si o parametrech a využití úlohy dekomprimovat MSBuild, která debalí archiv zip do zadaného umístění.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 213d37108e37b9002b2241e6c0806d6d7db7caf6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902489"
---
# <a name="unzip-task"></a>Unzip – úloha

Rozbalí archiv *zip* do zadaného umístění.

>[!NOTE]
>Tato `Unzip` úloha je k dispozici pouze v MSBuild 15,8 a vyšších.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Unzip` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFolder`|Povinný <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Určuje cílovou složku, do které se má soubor rozbalit.|
|`OverwriteReadOnlyFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , přepíše soubory jen pro čtení. Výchozí hodnota je `false` .|
|`SkipUnchangedFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , přeskočí soubory rozzipovává, které se nezměnily. Výchozí hodnota je `true` . Úloha `Unzip` považuje soubory za nezměněné, pokud mají stejnou velikost a je uveden stejný čas poslední aktualizace.|
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje jeden nebo více souborů, které mají být extrahovány. Při zadávání více souborů, které jsou extrahovány, do stejné složky.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

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

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
