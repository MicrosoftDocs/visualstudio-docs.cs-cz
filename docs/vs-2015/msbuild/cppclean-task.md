---
title: Úloha CPPClean – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: bddba1170cf675b5bde7ab8deed8cce1e7eb57dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196579"
---
# <a name="cppclean-task"></a>CPPClean – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odstraní dočasné soubory, které nástroj MSBuild vytvoří při sestavení projektu Visual C++. Proces odstraňování souborů sestavení se označuje jako *čištění*.  

## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **CPPClean –** .  

|            Parametr            |                                                                                                Popis                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Volitelný `ITaskItem[]` výstupní parametr.<br /><br /> Definuje pole položek výstupních souborů MSBuild, které mohou být spotřebovány a generovány úlohami.                                |
|          **DoDelete**           |                                                            Volitelný **logický** parametr.<br /><br /> Pokud `true` se čistí dočasné soubory sestavení.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Požadovaný parametr `String`.<br /><br /> Určuje středníky oddělený seznam přípon souborů, které se mají vyčistit.                                             |
|   **FilesExcludedFromClean**    |                                                    Volitelný `String` parametr.<br /><br /> Určuje středníky oddělený seznam souborů, které se nemají vyčistit.                                                    |
|       **FoldersToClean**        | Požadovaný parametr `String`.<br /><br /> Určuje středníky oddělený seznam adresářů, které se mají vyčistit. Můžete zadat úplnou nebo relativní cestu a cesta může obsahovat zástupný symbol ( **\\** \* ). |

## <a name="remarks"></a>Poznámky  

## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
