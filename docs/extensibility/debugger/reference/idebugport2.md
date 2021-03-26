---
description: Toto rozhraní představuje port pro ladění v počítači.
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d0b173f362418171def93ee92e3883b2910ad18
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087337"
---
# <a name="idebugport2"></a>IDebugPort2
Toto rozhraní představuje port pro ladění v počítači.

## <a name="syntax"></a>Syntax

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní, aby představovalo port pro ladění v počítači.

 Pokud port podporuje odesílání událostí portů, musí také implementovat <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní pro podporu <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní, které zase poskytuje rozhraní [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) nebo [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) vrací toto rozhraní, které představuje požadovaný port.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugPort2` .

|Metoda|Popis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Vrátí název portu.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Vrátí identifikátor portu.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Vrátí požadavek použitý k vytvoření portu (Pokud je k dispozici).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Vrátí dodavatele portu pro tento port.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Vrátí rozhraní pro proces daného identifikátoru procesu.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Vytvoří výčet všech procesů spuštěných na portu.|

## <a name="remarks"></a>Poznámky
 Místní port poskytuje přístup ke všem procesům a programům, které jsou spuštěné v místním počítači. Ostatní porty mohou představovat připojení sériového kabelu k zařízení se systémem systém Windows CE nebo síťové připojení k počítači, který není typu DCOM. `IDebugPort2`Rozhraní se používá k vyhledání názvu a identifikátoru portu a k zobrazení výčtu všech procesů spuštěných na portu. Zařízení pro spouštění a ukončování procesů na portu jsou implementovaná v `IDebugPortEx2` rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
