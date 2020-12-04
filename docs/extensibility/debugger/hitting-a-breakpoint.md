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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560847"
---
# <a name="hit-a-breakpoint"></a>Stiskněte zarážku
V následující části je popsán proces, když ladicí stroj (DE) narazí na zarážku při běhu nebo krokování:

## <a name="troubleshoot-a-hit-breakpoint"></a>Řešení potíží se zarážkou volání

1. DE pošle rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Správce ladění relace (SDM) volá [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby získal zarážku, ke které došlo.

## <a name="see-also"></a>Viz také:
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
