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
ms.openlocfilehash: 827014e04c23239274e31b994fd0178cbe8e5883
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596070"
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

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
