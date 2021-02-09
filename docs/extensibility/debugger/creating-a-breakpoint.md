---
title: Vytváření zarážky | Microsoft Docs
description: Přečtěte si o voláních metody, které správce ladění relace provede, když je načten modul potřebný k vytvoření vazby zarážky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dcd81b79fa43d86036a7fd1ac0ad813e6e2ebb78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894969"
---
# <a name="create-a-breakpoint"></a>Vytvořit zarážku
Následující popis popisuje proces vytvoření zarážky.

## <a name="methods-in-breakpoint-creation"></a>Metody při vytváření zarážek
 Když je načten modul, který je potřeba k navázání zarážky, zavolá Správce ladění relace (SDM) následující metody:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** se volá pouze v případě, že uživatel vytvoří zarážku z okna **zarážky** .

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Viz také
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
