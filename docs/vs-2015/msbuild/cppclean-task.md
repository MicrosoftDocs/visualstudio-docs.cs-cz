---
title: Cppclean – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a96571cbc4de4281daddd42f4b1d53b60b300e53
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826944"
---
# <a name="cppclean-task"></a>CPPClean – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Odstraní dočasné soubory, které MSBuild vytvoří při vytváření projektu Visual C++. Proces odstraňování souborů sestavení se označuje jako *čištění*.  

## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **cppclean –** úloh.  


|            Parametr            |                                                                                                Popis                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Volitelné `ITaskItem[]` výstupní parametr.<br /><br /> Definuje pole objektů MSBuild výstupní soubor položky, které lze používat a, protože ho vygeneroval úlohy.                                |
|          **DoDelete**           |                                                            Volitelné **logická** parametru.<br /><br /> Pokud `true`, čištění dočasné soubory sestavení.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Vyžaduje `String` parametru.<br /><br /> Určuje středníky oddělený seznam přípon souborů souborů k vyčištění.                                             |
|   **FilesExcludedFromClean**    |                                                    Volitelné `String` parametru.<br /><br /> Určuje středníky oddělený seznam souborů nechcete vyčistit.                                                    |
|       **FoldersToClean**        | Vyžaduje `String` parametru.<br /><br /> Určuje středníky oddělený seznam adresářů pro vyčištění. Můžete zadat úplnou nebo relativní cestu a cestu může obsahovat zástupný znak (**\\**\*). |

## <a name="remarks"></a>Poznámky  

## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



