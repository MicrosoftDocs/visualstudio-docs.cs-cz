---
title: Úloha CreateCSharpManifestResourceName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8e72ef282911ecb36fb9a16838f6cc311e253e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634354"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName – úloha

Vytvoří název manifestu ve stylu C# z daného názvu souboru *RESX* nebo jiného prostředku.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry [úlohy CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).

| Parametr | Popis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]` výstupní parametr jen pro čtení.<br /><br /> Výsledné názvy manifestů. |
| `ResourceFiles` | Požadovaný parametr `String`.<br /><br /> Název souboru prostředků, ze kterého chcete vytvořit název manifestu Jazyka C#. |
| `RootNamespace` | Volitelný `String` parametr.<br /><br /> Kořenový obor názvů souboru prostředků, obvykle převzatý ze souboru projektu. Může `null`být . |
| `PrependCultureAsDirectory` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`je název jazykové verze přidán jako název adresáře těsně před název prostředku manifestu. Výchozí hodnota `true`je . |
| `ResourceFilesWithManifestResourceNames` | Volitelný výstupní `String` parametr jen pro čtení.<br /><br /> Vrátí název souboru prostředků, který nyní obsahuje název prostředku manifestu. |

## <a name="remarks"></a>Poznámky

 [Úloha CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) určuje příslušný název prostředku manifestu, který má být přiřazen danému souboru *Resx* nebo jinému souboru prostředků. Úloha poskytuje logický název souboru prostředků a pak jej připojí k výstupnímu parametru jako metadata.

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
