---
title: Ukončení a odpojení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712493"
---
# <a name="termination-and-detaching"></a>Ukončení a odpojení
Následující část popisuje normální ukončení.

## <a name="discussion"></a>Diskuse
 Po pokračování rozhraní [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) nebo [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , pokud neexistují žádné zarážky, výjimky, chyby za běhu nebo nekonečné smyčky v aplikaci, která se má ladit, je program laděn na dokončení. Tento proces je normálním ukončením.

 K implementaci normálního ukončení musíte odeslat [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Normální ukončení vyžaduje spuštění metody [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Viz také
- [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)
