---
title: Findinlist – úloha | Dokumentace Microsoftu
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4a9d6a1fc6dbf8f160400ffae10a4a5fb355f3d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206801"
---
# <a name="findinlist-task"></a>FindInList – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V zadaném seznamu vyhledá položku, která má odpovídající itemspec.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry [findinlist – úloha](../msbuild/findinlist-task.md).  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`CaseSensitive`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, hledání se malá a velká písmena; jinak vrátí hodnotu, není. Výchozí hodnota je `true`.|  
|`FindLastMatch`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vraťte poslední shody; jinak vrátí první shoda. Výchozí hodnota je `false`.|  
|`ItemFound`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` jen pro čtení výstupního parametru.<br /><br /> První odpovídající položka nalezena v seznamu, pokud existuje.|  
|`ItemSpecToFind`|Vyžaduje `String` parametru.<br /><br /> Itemspec pro hledání.|  
|`List`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam, ve kterých chcete hledat itemspec.|  
|`MatchFileNameOnly`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, porovnávat pouze soubor název část itemspec; v opačném případě porovnání celý itemspec. Výchozí hodnota je `true`.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



