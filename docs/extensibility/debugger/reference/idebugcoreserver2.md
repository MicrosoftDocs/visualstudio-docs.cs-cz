---
description: Toto rozhraní slouží k reprezentaci a získání informací ze serveru v počítači v síti.
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 871f7ea5671fa4f3c615d84e0591bd331f945ccc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163132"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Toto rozhraní slouží k reprezentaci a získání informací ze serveru v počítači v síti.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní pro reprezentaci serveru. Každá instance aplikace Visual Studio vytvoří instanci tohoto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Vlastní dodavatel portu obdrží toto rozhraní při volání [události](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Ladicí stroj může toto rozhraní získat nepřímo prostřednictvím volání metody [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (který vrací [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), rozhraní, které je odvozeno z `IDebugCoreServer2` ).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugCoreServer2` .

|Metoda|Popis|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Získá název a atributy počítače.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Získá název počítače.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Získá dodavatele portu, který existuje v počítači.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Načte port, který již na počítači existuje.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Vytvoří enumerátor pro všechny porty v počítači.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Vytvoří enumerátor pro všechny dodavatele portů v počítači.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Načte pomůcky počítače pro počítač.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní používá aplikace Visual Studio také k procházení procesů spuštěných v počítačích v síti.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
