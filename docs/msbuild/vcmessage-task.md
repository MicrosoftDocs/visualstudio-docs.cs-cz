---
title: Úkol Zprávy VC | Dokumenty společnosti Microsoft
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631208"
---
# <a name="vcmessage-task"></a>VCMessage – úloha

Protokoly upozornění a chybové zprávy během sestavení.

## <a name="remarks"></a>Poznámky

 Tento úkol pomáhá implementovat msbuild pro projekty jazyka C++ a není určen k volání uživatelem. Další informace naleznete v tématu <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **VCMessage.**

|Parametr|Popis|
|---------------|-----------------|
|**Argumenty**|Volitelný **parametr String.**<br /><br /> Středník-oddělený seznam zpráv, které mají být zobrazeny.|
|**kód**|Povinný **parametr String.**<br /><br /> Číslo chyby, která kvalifikuje zprávu.|
|**Typ**|Volitelný **parametr String.**<br /><br /> Určuje druh zprávy, která má být vyzařována. Zadejte buď "Upozornění" pro vyzařující varovnou zprávu, nebo "Chyba" pro vyzařující chybovou zprávu.|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
