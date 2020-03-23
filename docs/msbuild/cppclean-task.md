---
title: CPPClean Úkol | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634341"
---
# <a name="cppclean-task"></a>CPPClean – úloha

Odstraní dočasné soubory, které msbuild vytvoří při sestavení projektu Jazyka C++. Proces odstranění souborů sestavení se označuje jako *čištění*.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **CPPClean.**

|Parametr|Popis|
|---------------|-----------------|
|**Odstraněné soubory**|Volitelný `ITaskItem[]` výstupní parametr.<br /><br /> Definuje pole položek výstupního souboru MSBuild, které mohou být spotřebovány a vydávány úkoly.|
|**DoDelete**|Volitelný **logický** parametr.<br /><br /> Pokud `true`vyčistěte dočasné soubory sestavení.|
|**FilePatternsToDeleteOnClean**|Požadovaný parametr `String`.<br /><br /> Určuje seznam, který se má vyčistit, podle středníku oddělených souborů.|
|**SouboryVyloučenoFromClean**|Volitelný `String` parametr.<br /><br /> Určuje seznam souborů oddělených středníkem, které se nemají čistit.|
|**SložkyToClean**|Požadovaný parametr `String`.<br /><br /> Určuje seznam adresářů oddělených středníkem, který má být vyčištěn. Můžete určit úplnou nebo relativní cestu a cesta může obsahovat zástupný symbol (*).|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
