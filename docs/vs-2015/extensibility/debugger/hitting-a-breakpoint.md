---
title: Zasáhne zarážku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152697"
---
# <a name="hitting-a-breakpoint"></a>Dosažení zarážky
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující článek popisuje proces, když ladicí stroj (DE) narazí na zarážku při běhu nebo krokování:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Řešení potíží se zarážkou volání  
  
1. DE pošle rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.  
  
2. Správce ladění relace (SDM) volá [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby získal zarážku, ke které došlo.  
  
## <a name="see-also"></a>Viz také  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
