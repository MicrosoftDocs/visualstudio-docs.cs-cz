---
title: Úloha WriteCodeFragment – | Microsoft Docs
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
ms.openlocfilehash: 3745e1c2f300c860d281752a0bf81359806c5d5e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567395"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment – úloha
Vygeneruje dočasný soubor kódu ze zadaného vygenerovaného fragmentu kódu. Neodstraní soubor.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `WriteCodeFragment`.

|Parametr|Popis|
|---------------|-----------------|
|`AssemblyAttributes`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Popis atributů, které mají být zapsány. Položka `Include` hodnota je úplný název typu atributu, například "System. AssemblyVersionAttribute".<br /><br /> Každá metadata představuje dvojici název-hodnota parametru, který musí být typu `String`. Některé atributy umožňují Poziční argumenty konstruktoru. Můžete však použít takové argumenty v jakémkoli atributu. Chcete-li nastavit atributy pozičního konstruktoru, použijte názvy metadat, které se podobají "_Parameter1", "_Parameter2" atd.<br /><br /> Index parametru nelze přeskočit.|
|`Language`|Vyžaduje se `String` parametr.<br /><br /> Určuje jazyk kódu, který se má vygenerovat.<br /><br /> `Language` může být libovolný jazyk, pro který je k dispozici zprostředkovatel CodeDom, například "C#" nebo "VisualBasic". Vygenerovaný soubor bude mít pro tento jazyk výchozí příponu názvu souboru.|
|`OutputDirectory`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje cílovou složku pro generovaný kód, obvykle mezilehlé složky.|
|`OutputFile`|Volitelný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje cestu k souboru, který se vygeneroval. Pokud je tento parametr nastaven pomocí názvu souboru, je cílová složka k názvu souboru. Pokud je tato složka nastavená pomocí kořenového adresáře, bude se cílová složka ignorovat.<br /><br /> Pokud tento parametr není nastaven, název výstupního souboru je cílová složka, libovolný název souboru a výchozí přípona názvu souboru pro zadaný jazyk.|

## <a name="remarks"></a>Poznámky
 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
