---
title: Úloha FindInList – | Microsoft Docs
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1fdbc29cfe2fb7d387c6f261953930d2f528150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149724"
---
# <a name="findinlist-task"></a>FindInList – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V zadaném seznamu najde položku, která má odpovídající itemspec.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry [úlohy FindInList –](../msbuild/findinlist-task.md).  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`CaseSensitive`|Volitelný `Boolean` parametr.<br /><br /> V případě `true` , že vyhledávání rozlišuje velká a malá písmena; v opačném případě ne. Výchozí hodnota je `true` .|  
|`FindLastMatch`|Volitelný `Boolean` parametr.<br /><br /> `true`Vrátí poslední shodu. v opačném případě vrátí první shodu. Výchozí hodnota je `false` .|  
|`ItemFound`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> První shodná položka, která se nachází v seznamu, pokud existuje.|  
|`ItemSpecToFind`|Požadovaný parametr `String`.<br /><br /> ItemSpec, který se má vyhledat.|  
|`List`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam, ve kterém se má hledat ItemSpec|  
|`MatchFileNameOnly`|Volitelný `Boolean` parametr.<br /><br /> IF `true` se shoduje s pouze částí názvu souboru ItemSpec. v opačném případě se porovná s celým ItemSpec. Výchozí hodnota je `true` .|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
