---
title: Úloha WriteCodeFragment | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ab604b23a99ab2dd62adca6076168fe264ab1b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630689"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment – úloha

Generuje dočasný soubor kódu ze zadaného fragmentu generovaného kódu. Neodstraní soubor.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `WriteCodeFragment` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AssemblyAttributes`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Popis atributů, které mají být zapsány. Hodnota `Include` položky je úplný název typu atributu, například "System.AssemblyVersionAttribute".<br /><br /> Každé metadato je dvojice název-hodnota parametru, který `String`musí být typu . Některé atributy povolují pouze argumenty pozičního konstruktoru. Tyto argumenty však můžete použít v libovolném atributu. Chcete-li nastavit atributy pozičníkonstruktoru, použijte názvy metadat, které se podobají "_Parameter1", "_Parameter2" a tak dále.<br /><br /> Index parametrů nelze přeskočit.|
|`Language`|Požadovaný parametr `String`.<br /><br /> Určuje jazyk kódu, který má být generován.<br /><br /> `Language`může být libovolný jazyk, pro který codedom zprostředkovatelje k dispozici, například "C#" nebo "VisualBasic". Vyzařovaný soubor bude mít výchozí příponu názvu souboru pro tento jazyk.|
|`OutputDirectory`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje cílovou složku pro generovaný kód, obvykle zprostředkující složku.|
|`OutputFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje cestu k souboru, který byl vygenerován. Pokud je tento parametr nastaven pomocí názvu souboru, je cílová složka před názvem souboru. Pokud je nastavenpomocí kořenového adresáře, cílová složka je ignorována.<br /><br /> Pokud tento parametr není nastaven, výstupní název souboru je cílová složka, libovolný název souboru a výchozí přípona názvu souboru pro zadaný jazyk.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
