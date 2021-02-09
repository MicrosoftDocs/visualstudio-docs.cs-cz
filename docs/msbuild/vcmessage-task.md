---
title: Úloha VCMessage – | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu VCMessage – k protokolování upozornění a chybových zpráv během sestavení pro projekty v jazyce C++.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8db60044080726b61a02a59cad68d93f683e282
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908829"
---
# <a name="vcmessage-task"></a>VCMessage – úloha

Zaznamená upozornění a chybové zprávy během sestavení.

## <a name="remarks"></a>Poznámky

 Tato úloha pomáhá implementovat MSBuild pro projekty v jazyce C++ a není určena pro volání uživatelem. Další informace naleznete v tématu <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **VCMessage –** .

|Parametr|Popis|
|---------------|-----------------|
|**Argumenty**|Volitelný **řetězcový** parametr.<br /><br /> Seznam zpráv, které se mají zobrazit, oddělený středníkem.|
|**Kód**|Povinný parametr **řetězce**<br /><br /> Číslo chyby, která tuto zprávu kvalifikuje.|
|**Typ**|Volitelný **řetězcový** parametr.<br /><br /> Určuje druh zprávy, která se má vygenerovat. Chcete-li vygenerovat zprávu s upozorněním, zadejte buď "Warning", nebo "Error" (chyba).|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
