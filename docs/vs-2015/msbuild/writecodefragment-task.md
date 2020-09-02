---
title: Úloha WriteCodeFragment – | Microsoft Docs
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
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa9882d30a8483937f77da21bb4700d4899a68a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555475"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
