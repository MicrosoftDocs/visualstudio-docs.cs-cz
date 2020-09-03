---
title: Přesunout úlohu | Microsoft Docs
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab75ccebd618946454c3386f564e3f6199409935
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191573"
---
# <a name="move-task"></a>Move – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přesune soubory do nového umístění.  
  
## <a name="parameters"></a>Parametry  
 Tabulka tato popisuje parametry `Move` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`DestinationFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje seznam souborů, do kterých se mají přesunout zdrojové soubory. V tomto seznamu se očekává mapování 1:1 na seznam, který je zadaný v `SourceFiles` parametru. To znamená, že první soubor zadaný v `SourceFiles` bude přesunut do prvního umístění určeného v a `DestinationFiles` tak dále.|  
|`DestinationFolder`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje adresář, do kterého chcete soubory přesunout.|  
|`MovedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky, které byly úspěšně přesunuty.|  
|`OverwriteReadOnlyFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , přepíše soubory i v případě, že jsou označeny jako soubory jen pro čtení.|  
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které se mají přesunout.|  
  
## <a name="remarks"></a>Poznámky  
 `DestinationFolder` `DestinationFiles` Musí být zadán buď parametr, nebo parametr, ale ne oba. Jsou-li zadány oba parametry, úloha se nezdaří a je zaznamenána chyba.  
  
 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
