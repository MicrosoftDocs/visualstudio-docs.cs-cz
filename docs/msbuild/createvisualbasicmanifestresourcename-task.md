---
title: Úloha CreateVisualBasicManifestResourceName – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6aa419001d2e890c87873862f0575607b31d22c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634289"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName – úloha

Vytvoří název manifestu ve stylu Visual Basic z daného názvu souboru *. resx* nebo jiného prostředku.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry [úlohy CreateVisualBasicManifestResourceName –](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametr | Popis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`výstup parametru jen pro čtení<br /><br /> Výsledné názvy manifestu. |
| `ResourceFiles` | Požadovaný parametr `String`.<br /><br /> Název souboru prostředků, ze kterého má být vytvořen Visual Basic název manifestu. |
| `RootNamespace` | Volitelný `String` parametr.<br /><br /> Kořenový obor názvů souboru prostředků, který se obvykle povede ze souboru projektu. Může být `null` . |
| `PrependCultureAsDirectory` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je název jazykové verze přidán jako název adresáře těsně před názvem prostředku manifestu. Výchozí hodnota je `true` . |
| `ResourceFilesWithManifestResourceNames` | Volitelný výstupní parametr jen pro čtení `String` .<br /><br /> Vrátí název souboru prostředků, který teď obsahuje název prostředku manifestu. |

## <a name="remarks"></a>Poznámky

 [Úloha CreateVisualBasicManifestResourceName –](../msbuild/createvisualbasicmanifestresourcename-task.md) určuje vhodný název prostředku manifestu, který se má přiřadit k danému souboru *. resx* nebo jinému souboru prostředků. Úloha poskytuje logický název souboru prostředků a pak ho připojí k výstupnímu parametru jako metadata.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
