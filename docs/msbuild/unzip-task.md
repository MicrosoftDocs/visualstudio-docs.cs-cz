---
title: Rozbalení úkolu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: d331fda05e8655be0536a1e83d8309ae8c060b1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631507"
---
# <a name="unzip-task"></a>Rozbalit úkol

Rozbalí archiv *ZIP* do zadaného umístění.

>[!NOTE]
>Úloha `Unzip` je k dispozici pouze v msbuild 15.8 a vyšší.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Unzip` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFolder`|Povinný <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Určuje cílovou složku, do které chcete soubor rozbalit.|
|`OverwriteReadOnlyFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`přepíše soubory jen pro čtení. Výchozí hodnota `false`je na .|
|`SkipUnchangedFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`přeskočí rozepnutí souborů, které jsou beze změny. Výchozí hodnota `true`je na . Úloha `Unzip` považuje soubory za nezměněné, pokud mají stejnou velikost a je uveden stejný čas poslední aktualizace.|
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje jeden nebo více souborů, které chcete rozbalit. Při zadávání více souborů jsou rozbaleny, aby se do stejné složky.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad rozbalí archiv a přepíše všechny soubory jen pro čtení.

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
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
