---
title: Úloha DownloadFile | Microsoft Docs
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
ms.openlocfilehash: 06171f3a1543f6fa827c1b6fd477b992d099fff6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590472"
---
# <a name="downloadfile-task"></a>DownloadFile – úloha
Stáhne zadané soubory pomocí protokolu HTTP (Hyper-Text Transfer Protocol).

>[!NOTE]
>Úloha DownloadFile je k dispozici pouze v MSBuild 15,8 a vyšších.

## <a name="parameters"></a>Parametry
Následující tabulka popisuje parametry úlohy `DownloadFile`.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFileName`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Název, který se má použít pro stažený soubor.  Ve výchozím nastavení je název souboru odvozený z `SourceUrl` nebo na vzdáleném serveru.|
|`DestinationFolder`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje cílovou složku, do které se má soubor stáhnout.  Pokud je vytvořena složka, pokud neexistuje.|
|`DownloadedFile`|Volitelný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubor, který se stáhl.|
|`Retries`|Volitelný parametr `Int32`.<br /><br /> Určuje počet pokusů o stažení, pokud se všechny předchozí pokusy nezdařily. Výchozím nastavením je nula.|
|`RetryDelayMilliseconds`|Volitelný parametr `Int32`.<br /><br /> Určuje zpoždění v milisekundách mezi všemi potřebnými pokusy. Výchozí hodnota je 5000.|
|`SkipUnchangedFiles`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, přeskočí stahování souborů, které se nezměnily. Výchozí hodnota je `true`. `DownloadFile` úloha považuje soubory za nezměněné, pokud mají stejnou velikost a čas poslední změny podle vzdáleného serveru. <br /><br />**Poznámka:**  Ne všechny servery HTTP označují datum poslední změny souborů, což způsobí, že se soubor stáhne znovu.|
|`SourceUrl`|Vyžaduje se `String` parametr.<br /><br /> Určuje adresu URL, která se má stáhnout.|

## <a name="remarks"></a>Poznámky
Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
Následující příklad stáhne soubor a zahrne ho do `Content`ch položek před sestavením projektu.

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

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
