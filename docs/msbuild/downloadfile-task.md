---
title: Úloha DownloadFile | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
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
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14b5daafbc4c11547515b9d77be2877eb07bcb8b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945341"
---
# <a name="downloadfile-task"></a>Úloha DownloadFile
Soubory ke stažení zadané soubory pomocí technologie Hyper-Text přenos protokol (HTTP).

>[!NOTE]
>Pouze je k dispozici v MSBuild 15.8 a vyšší DownloadFile úloha.
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `DownloadFile` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`DestinationFileName`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Název, který se má použít pro stažený soubor.  Ve výchozím nastavení, název souboru je odvozen od `SourceUrl` nebo vzdálený server.|
|`DestinationFolder`|Vyžaduje <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje cílovou složku ke stažení souboru.  Pokud složka se vytvoří, pokud neexistuje.|
|`DownloadedFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje soubor, který jste stáhli.|
|`Retries`|Volitelné `Int32` parametru.<br /><br /> Určuje, kolik pokusů o stažení, pokud všechny předchozí pokusy nezdařily. Výchozím nastavením je nula.|  
|`RetryDelayMilliseconds`|Volitelné `Int32` parametru.<br /><br /> Určuje zpoždění v milisekundách mezi všechny nezbytnými pokusy o opakování. Výchozí hodnota je 5000.|  
|`SkipUnchangedFiles`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, přeskočí stahování souborů, které jsou beze změny. Výchozí hodnota je `true`. `DownloadFile` Úloh považuje soubory za nezměněné, pokud mají stejnou velikost a stejný čas podle vzdálený server poslední aktualizace. <br /><br />**Poznámka:** ne všechny servery HTTP označuje datum poslední změny souborů způsobí, že soubor ke stažení znovu.|
|`SourceUrl`|Vyžaduje `String` parametru.<br /><br /> Určuje adresu URL ke stažení.|
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad stáhne soubor a zahrnuje ho `Content` položek před sestavením projektu.
  
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
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
