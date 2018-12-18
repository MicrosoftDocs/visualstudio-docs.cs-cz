---
title: IDebugProcess2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b79a517682a5f50aff25df5cde15f8c589104782
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758100"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje proces, který běží na portu. Pokud port, který je na místní port, pak `IDebugProcess2` obvykle představuje fyzické procesu v místním počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno port. Tento vlastní port dodavatele pro správu programů jako skupinu. Toto rozhraní musí být implementované dodavatele portu.  
  
 Ladicí stroj také implementuje toto rozhraní, pokud podporuje spuštění programu prostřednictvím [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní je volán primárně správce ladění relace (SDM) aby bylo možné pracovat se skupinou programy uvedené v tomto procesu.  
  
 Volání [getprocess –](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) nebo [getprocess –](../../../extensibility/debugger/reference/idebugport2-getprocess.md) zobrazíte toto rozhraní. Toto rozhraní je také vrácen voláním `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugProcess2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Získá popis procesu.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Vytvoří výčet programy, které jsou součástí tohoto procesu.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Získá název, jméno nebo název souboru procesu.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Získá instanci objektu počítače serveru, který tento proces je spuštěn na.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Ukončí proces.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Připojí se k procesu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Určuje, pokud SDM můžete odpojit proces.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Odpojí z procesu ladicího programu.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Získá identifikátor procesu systému.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Získá globálně jedinečný identifikátor pro tento proces.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [ZASTARALÉ]|Získá název relace, která je ladění procesu.<br /><br /> [ZASTARALÉ. BY MĚL VRÁTIT VŽDY `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Vytvoří výčet vlákna spuštěná v procesu.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Požadavky programu další spouštění kódu v této zastavit proces.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Získá port, který tento proces spuštěn.|  
  
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

