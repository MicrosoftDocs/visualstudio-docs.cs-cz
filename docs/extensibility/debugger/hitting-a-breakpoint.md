---
title: Zasáhne zarážku | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738563"
---
# <a name="hit-a-breakpoint"></a>Stiskněte zarážku
V následující části je popsán proces, když ladicí stroj (DE) narazí na zarážku při běhu nebo krokování:

## <a name="troubleshoot-a-hit-breakpoint"></a>Řešení potíží se zarážkou volání

1. DE pošle rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Správce ladění relace (SDM) volá [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby získal zarážku, ke které došlo.

## <a name="see-also"></a>Viz také
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
