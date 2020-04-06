---
title: IDebugEventCallback2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729882"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Toto rozhraní používá ladicí modul (DE) k odeslání ladicích událostí do správce ladění relace (SDM).

## <a name="syntax"></a>Syntaxe

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementuje toto rozhraní pro příjem událostí z ladicího modulu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Ladicí modul obvykle obdrží toto rozhraní při volání SDM [Připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)nebo [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Ladicí modul odesílá události do sdm voláním [Události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugEventCallback2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Odešle oznámení o událostech ladění do sdm.|

## <a name="remarks"></a>Poznámky
 Přestože [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) `IDebugEventCallback2` určit, že mají rozhraní, to není případ a ukazatel rozhraní bude vždy nulovou hodnotu. Místo toho ladicí modul `IDebugEventCallback2` musí použít rozhraní přijaté ve volání [Připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)nebo [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Pokud balíček implementuje [IDebugCallCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) ve spravovaném <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> kódu, důrazně doporučujeme, aby se vyvolána na různých rozhraních, které jsou předány [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
