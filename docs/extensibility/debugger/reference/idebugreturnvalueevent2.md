---
title: IDebugReturnValueEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0afc4284795ae8dcae7b41d9207ddc6e7c11e67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720249"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
Toto rozhraní je odesláno ladicí modul (DE) do správce ladění relace (SDM) po krokování z nebo přes funkci.

## <a name="syntax"></a>Syntaxe

```
IDebugReturnValueEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní pro hlášení vrácené hodnoty z funkce, která byla vyřazena z nebo nad. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události hlásit vrácenou hodnotu funkce. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm, když je připojen k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce je `IDebugReturnValueEvent2`uvedena metoda .

|Metoda|Popis|
|------------|-----------------|
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Získá hodnotu vrácenou při krokování z funkce.|

## <a name="remarks"></a>Poznámky
 Hodnotu vrácenou funkcí lze získat voláním [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md). Vrácená hodnota se zobrazí v okně **Autos.**

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
