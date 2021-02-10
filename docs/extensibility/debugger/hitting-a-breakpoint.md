---
title: Zasáhne zarážku | Microsoft Docs
description: Tento článek popisuje proces, který se provede, když ladicí stroj při spuštění nebo krokování narazí na zarážku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 808bf95631bb4106d071c29d7af233d071ef5229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947720"
---
# <a name="hit-a-breakpoint"></a>Stiskněte zarážku
V následující části je popsán proces, když ladicí stroj (DE) narazí na zarážku při běhu nebo krokování:

## <a name="troubleshoot-a-hit-breakpoint"></a>Řešení potíží se zarážkou volání

1. DE pošle rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Správce ladění relace (SDM) volá [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby získal zarážku, ke které došlo.

## <a name="see-also"></a>Viz také
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
