---
title: Odstraňuje se zarážka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738951"
---
# <a name="deleting-a-breakpoint"></a>Odstranění zarážky
Následující popis procesu při odstraňování nedokončené zarážky:

## <a name="deletion-process"></a>Proces odstranění
 Správce ladění relace (SDM) volá metodu [IDebugPendingBreakpoint2::D dstranit](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) , aby se odstranila nevyřízená zarážka a všechny svázané zarážky.

> [!NOTE]
> Jednu vázanou zarážku lze také odstranit voláním [IDebugBoundBreakpoint2::D dstranit](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Viz také
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
