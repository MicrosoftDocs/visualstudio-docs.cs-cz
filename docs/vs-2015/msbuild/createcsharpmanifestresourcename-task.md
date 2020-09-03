---
title: Úloha CreateCSharpManifestResourceName – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9308f94e865bfe54384719d8f57f3ad1819c79fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184043"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří [!INCLUDE[csprcs](../includes/csprcs-md.md)] název manifestu stylu z daného názvu souboru. resx nebo jiného prostředku.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry [úlohy CreateCSharpManifestResourceName –](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`výstup parametru jen pro čtení<br /><br /> Výsledné názvy manifestu.|  
|`ResourceFiles`|Požadovaný parametr `String`.<br /><br /> Název souboru prostředků, ze kterého má být vytvořen [!INCLUDE[csprcs](../includes/csprcs-md.md)] název manifestu.|  
|`RootNamespace`|Volitelný `String` parametr.<br /><br /> Kořenový obor názvů souboru prostředků, který se obvykle povede ze souboru projektu. Může být `null` .|  
|`PrependCultureAsDirectory`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je název jazykové verze přidán jako název adresáře těsně před názvem prostředku manifestu. Výchozí hodnota je `true` .|  
|`ResourceFilesWithManifestResourceNames`|Volitelný výstupní parametr jen pro čtení `String` .<br /><br /> Vrátí název souboru prostředků, který teď obsahuje název prostředku manifestu.|  
  
## <a name="remarks"></a>Poznámky  
 [Úloha CreateVisualBasicManifestResourceName –](../msbuild/createvisualbasicmanifestresourcename-task.md) určuje vhodný název prostředku manifestu, který se má přiřadit k danému souboru. resx nebo jinému souboru prostředků. Úloha poskytuje logický název souboru prostředků a pak ho připojí k výstupnímu parametru jako metadata.  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
