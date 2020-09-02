---
title: Odstraňuje se zarážka | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807120"
---
# <a name="deleting-a-breakpoint"></a>Odstranění zarážky
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující popis procesu při odstraňování nedokončené zarážky:  
  
## <a name="deletion-process"></a>Proces odstranění  
 Správce ladění relace (SDM) volá metodu [IDebugPendingBreakpoint2::D dstranit](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) , aby se odstranila nevyřízená zarážka a všechny svázané zarážky.  
  
> [!NOTE]
> Jednu vázanou zarážku lze také odstranit voláním [IDebugBoundBreakpoint2::D dstranit](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Viz také  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
