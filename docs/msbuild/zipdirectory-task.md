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
ms.openlocfilehash: 8c9a51fe097eb110e44b3f4bd932a26f4efb6ea6
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630636"
---
# <a name="zipdirectory-task"></a>ZipDirectory – úloha

Vytvoří archiv *zip* z obsahu adresáře.

>[!NOTE]
>Úkol `ZipDirectory` je k dispozici pouze v MSBuild 15,8 a vyšších.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `ZipDirectory`.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFile`|Povinný parametr <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Úplná cesta k souboru *. zip* , který se má vytvořit|
|`Overwrite`|Volitelný parametr `Boolean`.<br /><br /> Pokud se `true`, přeskočí cílový soubor, pokud existuje. Výchozí hodnota je `false`.|
|`SourceDirectory`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje adresář, ze kterého se má vytvořit archiv *zip.*|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad vytvoří archiv *zip* z výstupního adresáře po sestavení projektu.

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
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
