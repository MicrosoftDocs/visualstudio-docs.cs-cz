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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be4f963a5944882f14118be54e498fd4712c2e46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747188"
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
|**Textový**|Volitelný **řetězcový** parametr.<br /><br /> Určuje druh zprávy, která se má vygenerovat. Chcete-li vygenerovat zprávu s upozorněním, zadejte buď "Warning", nebo "Error" (chyba).|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)