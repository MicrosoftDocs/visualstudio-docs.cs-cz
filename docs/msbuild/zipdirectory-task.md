---
title: ZipDirectory Úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 5ceb23d34fab92fe0056f9bd82b9d9c63967dc4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094571"
---
# <a name="zipdirectory-task"></a>Úloha ZipDirectory

Vytvoří archiv *ZIP* z obsahu adresáře.

>[!NOTE]
>Úloha `ZipDirectory` je k dispozici pouze v msbuild 15.8 a vyšší.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ZipDirectory` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFile`|Povinný <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Úplná cesta k souboru *ZIP,* který chcete vytvořit.|
|`Overwrite`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`přeskočí cílový soubor bude přepsán, pokud existuje. Výchozí hodnota `false`je na .|
|`SourceDirectory`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje adresář, ze který má být archiv *zip* vytvářen.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad (pokud se používá jako importovaný soubor *.targets)* vytvoří archiv *ZIP* z výstupního adresáře po vytvoření projektu. Vlastnost `$(OutputPath)` by normálně být definovánv souboru projektu MSBuild, takže soubor projektu, který `output.zip`importuje následující soubor by vytvořit zip archiv :

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
