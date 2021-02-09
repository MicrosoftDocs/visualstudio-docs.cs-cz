---
title: Odstraňuje se zarážka | Microsoft Docs
description: Přečtěte si, jak Správce ladění relace odebere nevyřízenou zarážku a všechny svázané zarážky, které jsou z něj svázané, když se odstraní nevyřízená zarážka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862172"
---
# <a name="deleting-a-breakpoint"></a>Odstranění zarážky
Následující popis procesu při odstraňování nedokončené zarážky:

## <a name="deletion-process"></a>Proces odstranění
 Správce ladění relace (SDM) volá metodu [IDebugPendingBreakpoint2::D dstranit](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) , aby se odstranila nevyřízená zarážka a všechny svázané zarážky.

> [!NOTE]
> Jednu vázanou zarážku lze také odstranit voláním [IDebugBoundBreakpoint2::D dstranit](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Viz také
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
