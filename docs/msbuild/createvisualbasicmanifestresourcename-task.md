---
title: Vytvořit úlohu CreateVisualBasicManifestResourceName | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634289"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName – úloha

Vytvoří název manifestu ve stylu jazyka Visual Basic z daného názvu souboru *RESX* nebo jiného prostředku.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry [úlohy CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametr | Popis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]` výstupní parametr jen pro čtení.<br /><br /> Výsledné názvy manifestů. |
| `ResourceFiles` | Požadovaný parametr `String`.<br /><br /> Název souboru prostředků, ze kterého chcete vytvořit název manifestu jazyka Visual Basic. |
| `RootNamespace` | Volitelný `String` parametr.<br /><br /> Kořenový obor názvů souboru prostředků, obvykle převzatý ze souboru projektu. Může `null`být . |
| `PrependCultureAsDirectory` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`je název jazykové verze přidán jako název adresáře těsně před název prostředku manifestu. Výchozí hodnota `true`je . |
| `ResourceFilesWithManifestResourceNames` | Volitelný výstupní `String` parametr jen pro čtení.<br /><br /> Vrátí název souboru prostředků, který nyní obsahuje název prostředku manifestu. |

## <a name="remarks"></a>Poznámky

 [Úloha CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) určuje příslušný název prostředku manifestu, který má být přiřazen danému souboru *Resx* nebo jinému souboru prostředků. Úloha poskytuje logický název souboru prostředků a pak jej připojí k výstupnímu parametru jako metadata.

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
