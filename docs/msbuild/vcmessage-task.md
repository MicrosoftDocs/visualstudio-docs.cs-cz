---
title: Úloha VCMessage – | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631208"
---
# <a name="vcmessage-task"></a>VCMessage – úloha

Zaznamená upozornění a chybové zprávy během sestavení.

## <a name="remarks"></a>Poznámky

 Tato úloha pomáhá implementovat nástroj MSBuild C++ pro projekty a není určen pro volání uživatelem. Další informace naleznete v tématu <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **VCMessage –** .

|Parametr|Popis|
|---------------|-----------------|
|**Argumenty**|Volitelný **řetězcový** parametr.<br /><br /> Seznam zpráv, které se mají zobrazit, oddělený středníkem.|
|**Kód**|Povinný parametr **řetězce**<br /><br /> Číslo chyby, která tuto zprávu kvalifikuje.|
|**Typ**|Volitelný **řetězcový** parametr.<br /><br /> Určuje druh zprávy, která se má vygenerovat. Chcete-li vygenerovat zprávu s upozorněním, zadejte buď "Warning", nebo "Error" (chyba).|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
