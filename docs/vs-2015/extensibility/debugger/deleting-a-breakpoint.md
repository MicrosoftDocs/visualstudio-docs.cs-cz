---
title: Odstranění zarážky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b53be5e09d4579d95cb4b9d9726d6087effb8ff1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797387"
---
# <a name="deleting-a-breakpoint"></a>Odstranění zarážky
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující část popisuje proces při odstraňování čekající zarážkou:  
  
## <a name="deletion-process"></a>Proces odstraňování  
 Správce ladění relace (SDM) volá [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metoda odebrání čekající zarážka a všechny vazby zarážky vázán z něj.  
  
> [!NOTE]
>  Jeden vázaná zarážka může také odstranit volání [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Viz také  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)

