---
title: Chyby zarážky | Microsoft Docs
description: Přečtěte si o procesu, když se zarážka pokusí vytvořit vazby na kód, ale nefunguje a jak řešit chyby zarážek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a5003ce8abe79fcba9f9604047d2265810fda2
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914488"
---
# <a name="breakpoint-errors"></a>Chyby zarážky
Následující článek popisuje proces, když se zarážka pokusí vytvořit vazby na kód, ale neuspěje.

## <a name="troubleshoot-a-breakpoint-error"></a>Řešení potíží s chybou zarážky

1. Ladicí stroj (DE) odesílá [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do Správce ladění relace (SDM).

2. Volání SDM [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) k získání chyby zarážky.

3. Volání SDM [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) získá nevyřízenou zarážku, ze které pochází zarážka chyby.

4. Volání SDM [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) získat důvod, proč se zarážka chyby nepodařilo vytvořit.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
