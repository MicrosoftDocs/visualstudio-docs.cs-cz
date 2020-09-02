---
title: Krokování v režimu pozastavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423358"
---
# <a name="stepping-in-break-mode"></a>Krokování v režimu přerušení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující článek popisuje proces, který nastane, když je ladicí program v režimu pozastavení a musí procházet kód:  
  
## <a name="stepping-process"></a>Proces krokování  
  
1. Pro provedení kroku zavolejte [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) s argumenty [STEPKIND](../../extensibility/debugger/reference/stepkind.md) a [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) .  
  
2. Po dokončení kroku odešlete [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako událost zastavení.  
  
## <a name="see-also"></a>Viz také  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
