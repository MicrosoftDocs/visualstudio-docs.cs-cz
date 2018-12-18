---
title: Writecodefragment – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 862792e14bd52d52e3dafd83b4a8784f46ce8369
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290534"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Generuje soubor dočasný kód z fragmentu generovaného kódu. Nedojde k odstranění souboru.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `WriteCodeFragment` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AssemblyAttributes`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Popis atributů pro zápis. Položka `Include` hodnota je úplný název typu atributu, například "System.AssemblyVersionAttribute".<br /><br /> Každý metadata jsou dvojice název hodnota parametru, který musí být typu `String`. Některé atributy povolit pouze konstruktor poziční argumenty. Ale můžete použít tyto argumenty v jakéhokoliv atributu. Konstruktor poziční atributy, pomocí metadat názvy, které se podobají "_Parameter1", "_Parameter2" a tak dále.<br /><br /> Index parametru nemůže být přeskočeny.|  
|`Language`|Vyžaduje `String` parametru.<br /><br /> Určuje jazyk kódu pro generování.<br /><br /> `Language` může být libovolný jazyk pro které zprostředkovatel CodeDom je k dispozici, například "C" nebo "VisualBasic". Emitovaný soubor bude mít výchozí přípona názvu souboru pro daný jazyk.|  
|`OutputDirectory`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje cílovou složku pro vygenerovaný kód, obvykle zprostředkující složky.|  
|`OutputFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje cestu k souboru, který byl vygenerován. Pokud tento parametr je nastaven pomocí názvu souboru, cílová složka se přidá jako předpona k názvu souboru. Pokud je nastavena pomocí kořenové, cílová složka je ignorován.<br /><br /> Pokud tento parametr není nastaven, název výstupního souboru je cílovou složku, název libovolného souboru a výchozí přípona názvu souboru pro určený jazyk.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě s parametry, které jsou uvedené v tabulce, zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



