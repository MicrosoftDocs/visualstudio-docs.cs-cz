---
title: Krokování v režimu přerušení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712861"
---
# <a name="stepping-in-break-mode"></a>Krokování v režimu přerušení
Následující část popisuje proces, ke kterému dochází, když je ladicí program v režimu přerušení a musí procházet kódem:

## <a name="stepping-process"></a>Krokování proces

1. Volání [IDebugProgram2::Krok](../../extensibility/debugger/reference/idebugprogram2-step.md) s [STEPKIND](../../extensibility/debugger/reference/stepkind.md) a [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumenty pro spuštění kroku.

2. Po dokončení kroku odešlete [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako událost zastavení.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
