---
description: Toto rozhraní používá modul ladění (DE) k odesílání událostí ladění do Správce ladění relace (SDM).
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb33bcbdff14b0f95aab5d8f300473c13d4c342f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152907"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Toto rozhraní používá modul ladění (DE) k odesílání událostí ladění do Správce ladění relace (SDM).

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementuje toto rozhraní pro příjem událostí z ladicího stroje.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Ladicí stroj obvykle obdrží toto rozhraní, když volání SDM [připojí](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [připojí](../../../extensibility/debugger/reference/idebugengine2-attach.md)nebo [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Ladicí stroj odesílá události do modelu SDM voláním [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugEventCallback2` .

|Metoda|Popis|
|------------|-----------------|
|[Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Pošle oznámení o událostech ladění do SDM.|

## <a name="remarks"></a>Poznámky
 I když [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) určují, že přebírají `IDebugEventCallback2` rozhraní, toto není případ a ukazatel rozhraní bude vždy hodnota null. Místo toho musí ladicí stroj použít `IDebugEventCallback2` rozhraní přijaté ve volání k [připojení](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md)nebo [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Pokud balíček implementuje [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) ve spravovaném kódu, důrazně doporučujeme, abyste jej <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> vyvolali v různých rozhraních, která jsou předána [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
