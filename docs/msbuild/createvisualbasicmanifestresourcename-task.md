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
ms.openlocfilehash: 636cd4a7d287f60235f3827837050efa1e15eb90
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596915"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName – úloha
Vytvoří název manifestu ve stylu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]z daného názvu souboru *. resx* nebo jiného prostředku.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry [úlohy CreateVisualBasicManifestResourceName –](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametr | Popis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr s oprávněními jen pro čtení.<br /><br /> Výsledné názvy manifestu. |
| `ResourceFiles` | Vyžaduje se `String` parametr.<br /><br /> Název souboru prostředků, ze kterého má být vytvořen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] název manifestu. |
| `RootNamespace` | Volitelný parametr `String`.<br /><br /> Kořenový obor názvů souboru prostředků, který se obvykle povede ze souboru projektu. Může být `null`. |
| `PrependCultureAsDirectory` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, název jazykové verze se přidá jako název adresáře těsně před názvem prostředku manifestu. Výchozí hodnota je `true`. |
| `ResourceFilesWithManifestResourceNames` | Volitelný výstupní parametr `String` jen pro čtení.<br /><br /> Vrátí název souboru prostředků, který teď obsahuje název prostředku manifestu. |

## <a name="remarks"></a>Poznámky
 [Úloha CreateVisualBasicManifestResourceName –](../msbuild/createvisualbasicmanifestresourcename-task.md) určuje vhodný název prostředku manifestu, který se má přiřadit k danému souboru *. resx* nebo jinému souboru prostředků. Úloha poskytuje logický název souboru prostředků a pak ho připojí k výstupnímu parametru jako metadata.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
