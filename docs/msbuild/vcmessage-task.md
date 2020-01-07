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
ms.openlocfilehash: 66b1bf1eb222d70c18bfb94c65dddd2903864c68
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591109"
---
# <a name="vcmessage-task"></a>VCMessage – úloha
Zaznamená upozornění a chybové zprávy během sestavení.

## <a name="remarks"></a>Poznámky
 Tato úloha pomáhá implementovat nástroj MSBuild C++ pro projekty a není určen pro volání uživatelem. Další informace najdete v tématu <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy **VCMessage –** .

|Parametr|Popis|
|---------------|-----------------|
|**Argumenty**|Volitelný **řetězcový** parametr.<br /><br /> Seznam zpráv, které se mají zobrazit, oddělený středníkem.|
|**Kód**|Povinný parametr **řetězce**<br /><br /> Číslo chyby, která tuto zprávu kvalifikuje.|
|**Typ**|Volitelný **řetězcový** parametr.<br /><br /> Určuje druh zprávy, která se má vygenerovat. Chcete-li vygenerovat zprávu s upozorněním, zadejte buď "Warning", nebo "Error" (chyba).|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
