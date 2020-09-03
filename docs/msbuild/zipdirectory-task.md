---
title: Úloha ZipDirectory | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1092add6386ccc5bc1de78efcf7b623a617d920b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183064"
---
# <a name="zipdirectory-task"></a>ZipDirectory – úloha

Vytvoří archiv *zip* z obsahu adresáře.

>[!NOTE]
>Tato `ZipDirectory` úloha je k dispozici pouze v MSBuild 15,8 a vyšších.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ZipDirectory` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFile`|Povinný <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Úplná cesta k souboru *. zip* , který se má vytvořit|
|`Overwrite`|Volitelný `Boolean` parametr.<br /><br /> `true`V případě, že cílový soubor bude přepsán, pokud existuje. Výchozí hodnota je `false` .|
|`SourceDirectory`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje adresář, ze kterého se má vytvořit archiv *zip.*|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad (Pokud se používá jako importovaný soubor *. targets* ) vytvoří archiv *zip* z výstupního adresáře po sestavení projektu. `$(OutputPath)`Vlastnost by se normálně definovala v souboru projektu MSBuild, takže soubor projektu, který importuje následující soubor, vytvoří archiv zip `output.zip` :

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
