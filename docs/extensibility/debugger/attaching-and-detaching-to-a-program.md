---
title: Připojení a odpojení programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd47e214492f0888d7780f8aef5944cdcdeb2591
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949731"
---
# <a name="attaching-and-detaching-to-a-program"></a>Připojení a odpojení programu
Připojování ladicího programu vyžaduje odeslání tak správné pořadí metod a událostí pomocí vlastních atributech.  
  
## <a name="sequence-of-methods-and-events"></a>Posloupnost metody a události  
  
1. Správce ladění relace (SDM) volá [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.  
  
    Na základě modelu procesu ladicí stroj (DE), `IDebugProgramNodeAttach2::OnAttach` metoda vrátí jednu z následujících metod, které určuje, co bude dál.  
  
    Pokud `S_FALSE` se vrátí ladicí stroj úspěšně připojí k programu. V opačném případě [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md) metoda je volána k dokončení procesu připojování.  
  
    Pokud `S_OK` se vrátí, DE je třeba načíst ve stejném procesu jako SDM. SDM provádí následující úlohy:  
  
   1.  Volání [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) získat informace pro modul DE.  
  
   2.  Společně vytvoří DE.  
  
   3.  Volání [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2. Odešle DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) k SDM s `EVENT_SYNC` atribut.  
  
3. Odešle DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) k SDM s `EVENT_SYNC` atribut. 
  
4. Odešle DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) k SDM s `EVENT_SYNC_STOP` atribut.  
  
   Odpojení od programu je jednoduché, dvoustupňový proces, následujícím způsobem:  
  
5. Volání SDM [odpojit](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
6. Odešle DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Viz také:  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)