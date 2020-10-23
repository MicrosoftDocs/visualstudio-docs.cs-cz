---
title: Úloha DownloadFile | Microsoft Docs
description: Přečtěte si o parametrech úlohy MSBuild DownloadFile, která stáhne zadané soubory pomocí protokolu HTTP.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fda3edcd1c8bf173e1b70d8bf2d76d58f6e10d8d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436649"
---
# <a name="downloadfile-task"></a>DownloadFile – úloha

Stáhne zadané soubory pomocí protokolu HTTP (Hyper-Text Transfer Protocol).

>[!NOTE]
>Úloha DownloadFile je k dispozici pouze v MSBuild 15,8 a vyšších.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `DownloadFile` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFileName`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Název, který se má použít pro stažený soubor.  Ve výchozím nastavení je název souboru odvozený z `SourceUrl` nebo ze vzdáleného serveru.|
|`DestinationFolder`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje cílovou složku, do které se má soubor stáhnout.  Pokud je vytvořena složka, pokud neexistuje.|
|`DownloadedFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje soubor, který se stáhl.|
|`Retries`|Volitelný `Int32` parametr.<br /><br /> Určuje počet pokusů o stažení, pokud se všechny předchozí pokusy nezdařily. Výchozím nastavením je nula.|
|`RetryDelayMilliseconds`|Volitelný `Int32` parametr.<br /><br /> Určuje zpoždění v milisekundách mezi všemi potřebnými pokusy. Výchozí hodnota je 5000.|
|`SkipUnchangedFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , přeskočí stahování souborů, které se nezměnily. Výchozí hodnota je `true` . Tato `DownloadFile` úloha posuzuje soubory, které mají být beze změny, pokud mají stejnou velikost a stejnou čas poslední změny v závislosti na vzdáleném serveru. <br /><br />**Poznámka:**  Ne všechny servery HTTP označují datum poslední změny souborů, což způsobí, že se soubor stáhne znovu.|
|`SourceUrl`|Požadovaný parametr `String`.<br /><br /> Určuje adresu URL, která se má stáhnout.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad stáhne soubor a zahrne ho do `Content` položek před sestavením projektu.

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
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
