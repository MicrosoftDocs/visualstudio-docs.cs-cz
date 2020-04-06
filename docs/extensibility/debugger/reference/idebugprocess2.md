---
title: IDebugProcess2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723795"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Toto rozhraní představuje proces spuštěný na portu. Pokud je port místní port, pak `IDebugProcess2` obvykle představuje fyzický proces v místním počítači.

## <a name="syntax"></a>Syntaxe

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno dodavatelem vlastního portu pro správu programů jako skupiny. Toto rozhraní musí být implementováno dodavatelem portu.

 Ladicí modul také implementuje toto rozhraní, pokud podporuje spuštění programu prostřednictvím [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je voláno především správcem ladění relace (SDM) za účelem interakce se skupinou programů identifikovaných v tomto procesu.

 Volání [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) nebo [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) získat toto rozhraní. Toto rozhraní je `IDebugEngineLaunch2::LaunchSuspended`také vrácena voláním .

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugProcess2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Získá popis procesu.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Vyjmenovává programy, které jsou obsaženy v tomto procesu.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Získá název, popisný název nebo název souboru procesu.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Získá instanci serveru počítače, na který je tento proces spuštěn.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Ukončí proces.|
|[Připojit](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Připojí se k procesu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Určuje, zda sdm může odpojit proces.|
|[Odpojit](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Odpojí ladicí program od procesu.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Získá identifikátor systémového procesu.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Získá globálně jedinečný identifikátor pro tento proces.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [ZASTARALÉ]|Získá název relace, která je ladění procesu.<br /><br /> [ZASTARALÉ. BY SE `E_NOTIMPL`MĚL VŽDY VRÁTIT .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Vyjmenovává vlákna spuštěná v procesu.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Požaduje, aby se zastavil další program spuštěný v tomto procesu.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Získá port, který je spuštěn v tomto procesu.|

## <a name="remarks"></a>Poznámky
 Obsahuje `IDebugProcess2` jedno nebo více rozhraní [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
