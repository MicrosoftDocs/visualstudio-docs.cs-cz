---
title: Odstranění zarážky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc85104ca02922c1a28152d75550a821598d7b1e
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203862"
---
# <a name="deleting-a-breakpoint"></a>Odstranění zarážky
Následující část popisuje proces při odstraňování čekající zarážkou:  
  
## <a name="deletion-process"></a>Proces odstraňování  
 Správce ladění relace (SDM) volá [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metoda odebrání čekající zarážka a všechny vazby zarážky vázán z něj.  
  
> [!NOTE]
>  Jeden vázaná zarážka může také odstranit volání [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Viz také:  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)