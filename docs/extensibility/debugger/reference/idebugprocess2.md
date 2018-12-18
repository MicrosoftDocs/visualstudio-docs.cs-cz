---
title: IDebugProcess2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77adecb0f3aef5a9c9d0fc8a05e6b44016dd9ae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121372"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Toto rozhraní představuje proces, který běží na portu. Jestliže port je místního portu, potom `IDebugProcess2` obvykle reprezentuje fyzický procesu v místním počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno modulem vlastní port dodavatele pro správu programy jako skupina. Toto rozhraní musí být implementované dodavatel portu.  
  
 Modul ladění také implementuje toto rozhraní, pokud ji podporuje spuštění programu prostřednictvím [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní je volána především správce ladicí relace (SDM) Chcete-li pracovat s skupinu programů identifikovat v tomto procesu.  
  
 Volání [getprocess –](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) nebo [getprocess –](../../../extensibility/debugger/reference/idebugport2-getprocess.md) získat toto rozhraní. Toto rozhraní je také vrácena voláním `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugProcess2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Získá popis procesu.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Vytvoří výčet programy, které jsou obsažené v tomto procesu.|  
|[GetName –](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Získá název, popisný název nebo název souboru procesu.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Získá instanci objektu, který tento proces běží na počítač serveru.|  
|[Ukončení](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Ukončit proces.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Připojí k procesu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Určuje, pokud SDM můžete odpojit proces.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Umožňuje odpojit ladicí program z procesu.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Získá identifikátor procesu systému.|  
|[Getprocessid –](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Získá globálně jedinečný identifikátor pro tento proces.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [ZASTARALÝ]|Získá název relace, který je ladění proces.<br /><br /> [ZASTARALÉ. MĚLI VŽDY VRÁTÍ `E_NOTIMPL`.]|  
|[Enumthreads –](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Vytvoří výčet vláken spuštěné v procesu.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Požadavky, které další program spuštění kódu v ukončení tohoto procesu.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Získá port, který tento proces běží na.|  
  
## <a name="remarks"></a>Poznámky  
 `IDebugProcess2` Obsahuje jeden nebo více [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Getprocess –](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Getprocess –](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Další](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Události](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)