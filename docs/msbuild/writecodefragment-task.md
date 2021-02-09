---
title: Úloha WriteCodeFragment – | Microsoft Docs
description: Přečtěte si, jak nástroj MSBuild používá úlohu WriteCodeFragment – k vygenerování dočasného souboru kódu ze zadaného fragmentu generovaného kódu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1bdab6066ce93475a2f6bb193c67da87c4fcaddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888079"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment – úloha

Vygeneruje dočasný soubor kódu ze zadaného vygenerovaného fragmentu kódu. Neodstraní soubor.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `WriteCodeFragment` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AssemblyAttributes`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Popis atributů, které mají být zapsány. Hodnota položky `Include` je úplný název typu atributu, například "System. AssemblyVersionAttribute".<br /><br /> Každá metadata tvoří dvojici název-hodnota parametru, který musí být typu `String` . Některé atributy umožňují Poziční argumenty konstruktoru. Můžete však použít takové argumenty v jakémkoli atributu. Chcete-li nastavit atributy pozičního konstruktoru, použijte názvy metadat, které se podobají "_Parameter1", "_Parameter2" atd.<br /><br /> Index parametru nelze přeskočit.|
|`Language`|Požadovaný parametr `String`.<br /><br /> Určuje jazyk kódu, který se má vygenerovat.<br /><br /> `Language` může to být libovolný jazyk, pro který je k dispozici zprostředkovatel CodeDom, například "C#" nebo "VisualBasic". Vygenerovaný soubor bude mít pro tento jazyk výchozí příponu názvu souboru.|
|`OutputDirectory`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje cílovou složku pro generovaný kód, obvykle mezilehlé složky.|
|`OutputFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje cestu k souboru, který se vygeneroval. Pokud je tento parametr nastaven pomocí názvu souboru, je cílová složka k názvu souboru. Pokud je tato složka nastavená pomocí kořenového adresáře, bude se cílová složka ignorovat.<br /><br /> Pokud tento parametr není nastaven, název výstupního souboru je cílová složka, libovolný název souboru a výchozí přípona názvu souboru pro zadaný jazyk.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
