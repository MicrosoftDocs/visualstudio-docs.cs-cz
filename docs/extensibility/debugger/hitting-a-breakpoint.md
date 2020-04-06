---
title: Zasažení zarážky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738563"
---
# <a name="hit-a-breakpoint"></a>Zásah do zarážky
Následující část popisuje proces, kdy ladicí modul (DE) narazí na zarážku při spuštění nebo krokování:

## <a name="troubleshoot-a-hit-breakpoint"></a>Poradce při potížích s zarážou přístupů

1. DE odešle rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Správce ladění relace (SDM) volá [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) získat zarážku, která byla přístupná.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
