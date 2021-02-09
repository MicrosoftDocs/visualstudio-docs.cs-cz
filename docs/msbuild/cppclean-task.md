---
title: Úloha CPPClean – | Microsoft Docs
description: Tento článek popisuje úlohu CPPClean –, která slouží k odstranění dočasných souborů, které nástroj MSBuild vytvoří při sestavení projektu C++.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5b3d48c4556cfd05e5ce3f2b893b3f0e9a07226
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901433"
---
# <a name="cppclean-task"></a>CPPClean – úloha

Odstraní dočasné soubory, které nástroj MSBuild vytvoří při sestavení projektu C++. Proces odstraňování souborů sestavení se označuje jako *čištění*.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **CPPClean –** .

|Parametr|Popis|
|---------------|-----------------|
|**DeletedFiles**|Volitelný `ITaskItem[]` výstupní parametr.<br /><br /> Definuje pole položek výstupních souborů MSBuild, které mohou být spotřebovány a generovány úlohami.|
|**DoDelete**|Volitelný **logický** parametr.<br /><br /> Pokud `true` se čistí dočasné soubory sestavení.|
|**FilePatternsToDeleteOnClean**|Požadovaný parametr `String`.<br /><br /> Určuje středníky oddělený seznam přípon souborů, které se mají vyčistit.|
|**FilesExcludedFromClean**|Volitelný `String` parametr.<br /><br /> Určuje středníky oddělený seznam souborů, které se nemají vyčistit.|
|**FoldersToClean**|Požadovaný parametr `String`.<br /><br /> Určuje středníky oddělený seznam adresářů, které se mají vyčistit. Můžete zadat úplnou nebo relativní cestu a cesta může obsahovat zástupný symbol (*).|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
