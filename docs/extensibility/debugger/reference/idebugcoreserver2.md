---
title: IDebugCoreServer2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5990c84fbaeb5ebb3b1e188d3317234afda06b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733034"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Toto rozhraní slouží k reprezentaci a získávání informací ze serveru v počítači v síti.

## <a name="syntax"></a>Syntaxe

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní představující server. Každá instance sady Visual Studio vytvoří instanci tohoto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Vlastní dodavatel portu obdrží toto rozhraní ve volání [události](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Ladicí modul může získat toto rozhraní nepřímo prostřednictvím volání [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (který vrací [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), rozhraní, které je odvozeno z `IDebugCoreServer2`).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugCoreServer2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Získá název a atributy počítače.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Získá název počítače.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Získá dodavatele portu, který existuje v počítači.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Získá port, který již existuje v počítači.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Vytvoří čítač výčtu pro všechny porty v počítači.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Vytvoří čítač pro všechny dodavatele portů v počítači.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Získá nástroje počítače pro počítač.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní používá také visual studio k procházení procesů spuštěných v počítačích v síti.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
