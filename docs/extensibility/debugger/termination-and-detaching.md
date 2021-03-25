---
title: Ukončení a odpojení | Microsoft Docs
description: Normální ukončení znamená, že se program, který se právě ladí, spouští bez zarážek, výjimek, chyb za běhu nebo nekonečné smyčky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8662809b50dbfec3046af1d0d6b6fa151c3a33e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057829"
---
# <a name="termination-and-detaching"></a>Ukončení a odpojení
Následující část popisuje normální ukončení.

## <a name="discussion"></a>Diskuse
 Po pokračování rozhraní [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) nebo [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , pokud neexistují žádné zarážky, výjimky, chyby za běhu nebo nekonečné smyčky v aplikaci, která se má ladit, je program laděn na dokončení. Tento proces je normálním ukončením.

 K implementaci normálního ukončení musíte odeslat [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Normální ukončení vyžaduje spuštění metody [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Viz také
- [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)
