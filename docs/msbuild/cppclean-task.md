---
title: Úloha CPPClean – | Microsoft Docs
ms.date: 11/04/2016
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
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 331a96c7cd67b933e521e3fe5f2d7a909ffa5d03
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634341"
---
# <a name="cppclean-task"></a>CPPClean – úloha

Odstraní dočasné soubory, které nástroj MSBuild vytvoří při C++ sestavení projektu. Proces odstraňování souborů sestavení se označuje jako *čištění*.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **CPPClean –** .

|Parametr|Popis|
|---------------|-----------------|
|**DeletedFiles**|Volitelný výstupní parametr `ITaskItem[]`.<br /><br /> Definuje pole položek výstupních souborů MSBuild, které mohou být spotřebovány a generovány úlohami.|
|**DoDelete**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, vyčistěte dočasné soubory sestavení.|
|**FilePatternsToDeleteOnClean**|Vyžaduje se `String` parametr.<br /><br /> Určuje středníky oddělený seznam přípon souborů, které se mají vyčistit.|
|**FilesExcludedFromClean**|Volitelný parametr `String`.<br /><br /> Určuje středníky oddělený seznam souborů, které se nemají vyčistit.|
|**FoldersToClean**|Vyžaduje se `String` parametr.<br /><br /> Určuje středníky oddělený seznam adresářů, které se mají vyčistit. Můžete zadat úplnou nebo relativní cestu a cesta může obsahovat zástupný symbol (*).|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
