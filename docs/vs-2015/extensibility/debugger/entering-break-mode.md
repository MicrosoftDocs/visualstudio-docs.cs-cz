---
title: Vstup do režimu přerušení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182255"
---
# <a name="entering-break-mode"></a>Přechod do režimu přerušení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující článek popisuje proces, ke kterému dochází, když je zjištěna zarážka po rozkrokování do funkce, spuštění na řádku zdrojového kódu, který obsahuje kurzor nebo je spuštěn na zarážku.  
  
## <a name="break-mode-process"></a>Proces režimu přerušení  
  
1. Ladicí stroj (DE) odesílá [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)nebo jakoukoliv jinou událost zastavení, aby mohl IDE přejít do režimu přerušení.  
  
2. Model SDM získá informace zásobníku volání z vlákna následujícím způsobem:  
  
    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    - [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) získat informace o zdrojovém kódu  
  
    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) pro získání názvu souboru  
  
    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) Získá rozsah příkazu.  
  
    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) získat informace o paměti  
  
## <a name="see-also"></a>Viz také  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
