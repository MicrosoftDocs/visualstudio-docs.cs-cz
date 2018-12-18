---
title: Rozbalte úloh | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
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
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f633e741cf72596708963d89973eb039b18b4e88
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151210"
---
# <a name="unzip-task"></a>Rozbalte úloh
Unzips *ZIP* archivní úrovně do zadaného umístění.

>[!NOTE]
>`Unzip` Úloh je k dispozici v MSBuild 15.8 a vyšší pouze.
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Unzip` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`DestinationFolder`|Vyžaduje <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Určuje cílovou složku dekomprimovat soubor.|
|`OverwriteReadOnlyFiles`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, přepíše soubory jen pro čtení. Výchozí hodnota je `false`.|
|`SkipUnchangedFiles`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, přeskočí rozzipovávání soubory, které jsou beze změny. Výchozí hodnota je `true`. Úloha `Unzip` považuje soubory za nezměněné, pokud mají stejnou velikost a je uveden stejný čas poslední aktualizace.|
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje jeden nebo více souborů k rozbalení. Při zadávání více souborů jsou rozbaleny v pořadí do stejné složky.|
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu unzips archiv a přepíše všechny soubory jen pro čtení.
  
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
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
