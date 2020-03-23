---
title: Úloha souboru DownloadFile | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81a9c3b1c22277261276ced1940f1f2e83d11882
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634250"
---
# <a name="downloadfile-task"></a>Úloha DownloadFile

Stáhne zadané soubory pomocí protokolu HTTP (Hyper-Text Transfer Protocol).

>[!NOTE]
>Úloha DownloadFile je k dispozici pouze v msbuild15.8 a vyšší.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `DownloadFile` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFileName`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Název, který má být pro stažený soubor používán.  Ve výchozím nastavení je název souboru odvozen ze vzdáleného `SourceUrl` serveru nebo ze vzdáleného serveru.|
|`DestinationFolder`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje cílovou složku, do které chcete soubor stáhnout.  Pokud je složka vytvořena, pokud neexistuje.|
|`DownloadedFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje soubor, který byl stažen.|
|`Retries`|Volitelný `Int32` parametr.<br /><br /> Určuje, kolikrát se pokusíte stáhnout, pokud se všechny předchozí pokusy nezdařily. Výchozím nastavením je nula.|
|`RetryDelayMilliseconds`|Volitelný `Int32` parametr.<br /><br /> Určuje zpoždění v milisekundách mezi všemi nezbytnými opakovanými pokusy. Výchozí hodnota je 5000.|
|`SkipUnchangedFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`přeskočí stahování souborů, které jsou beze změny. Výchozí hodnota `true`je na . Úloha `DownloadFile` považuje soubory za nezměněné, pokud mají stejnou velikost a stejný čas poslední změny podle vzdáleného serveru. <br /><br />**Poznámka:**  Ne všechny servery HTTP označují datum poslední změny souborů způsobí, že soubor bude znovu stažen.|
|`SourceUrl`|Požadovaný parametr `String`.<br /><br /> Určuje adresu URL ke stažení.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad stáhne soubor a zahrne jej do `Content` položek před sestavením projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
