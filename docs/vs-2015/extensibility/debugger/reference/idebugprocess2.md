---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68f1693bbbda9bbf7622c2378799db4a342be7a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187978"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje proces spuštěný na portu. Pokud je port místním portem, `IDebugProcess2` obvykle představuje fyzický proces na místním počítači.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno vlastním dodavatelem portu pro správu programů jako skupiny. Toto rozhraní musí být implementováno dodavatelem portu.  
  
 Ladicí stroj implementuje toto rozhraní také v případě, že podporuje spouštění programu prostřednictvím [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní se nazývá Správce ladění relace (SDM), aby bylo možné komunikovat se skupinou programů identifikovaných v tomto procesu.  
  
 Pro získání tohoto rozhraní volejte [Getprocess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) nebo [getprocess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) . Toto rozhraní je také vráceno voláním metody `IDebugEngineLaunch2::LaunchSuspended` .  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugProcess2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Získá popis procesu.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Vytvoří výčet programů, které jsou obsaženy v tomto procesu.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Získá název, popisný název nebo název souboru procesu.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Načte instanci počítačového serveru, na kterém tento proces běží.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) (Ukončení)|Ukončí proces.|  
|[Připojit](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Připojí se k procesu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Určuje, zda SDM může odpojit proces.|  
|[Odpojit](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Odpojí ladicí program od procesu.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Získá identifikátor systémového procesu.|  
|[GetProcessId –](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Získá globálně jedinečný identifikátor pro tento proces.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> ZASTARALÉ|Získá název relace, která provádí ladění procesu.<br /><br /> Zastaralé. VŽDY vracet `E_NOTIMPL` .]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Vytvoří výčet vláken spuštěných v procesu.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Požaduje, aby byl ukončen další program, který spouští kód v tomto procesu.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Získá port, na kterém tento proces běží.|  
  
## <a name="remarks"></a>Poznámky  
 `IDebugProcess2`Obsahuje jedno nebo více [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Getprocess –](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Getprocess –](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Generace](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Událostí](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Událostí](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
