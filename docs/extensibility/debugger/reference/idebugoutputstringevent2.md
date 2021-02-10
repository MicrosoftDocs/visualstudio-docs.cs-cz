---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8fa51311bb7548889cccdd2eb91e70a4679fb5de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953302"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Toto rozhraní je odesláno ladicím modulem (DE) do nástroje Session Debug Manager (SDM) pro výstup řetězce.

## <a name="syntax"></a>Syntax

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní k odeslání řetězce do okna **výstupu** rozhraní IDE. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události pro odeslání řetězce do okna **výstup** . Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojená k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Následující tabulka ukazuje metodu `IDebugOutputStringEvent2` .

|Metoda|Popis|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Načte zobrazitelnou zprávu.|

## <a name="remarks"></a>Poznámky
 Například v nespravovaném kódu může řetězec, který má být výstup, nacházet, pokud program, který ladíte, odesílá řetězec do `OutputDebugString` funkce Win32. Tento řetězec je zachycen nástrojem DE a odeslán do SDM jako `IDebugOutputStringEvent2` událost.

 K odeslání zprávy, která vyžaduje reakci uživatele, použijte [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) .

 K odeslání chybové zprávy, která nevyžaduje odpověď, použijte [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
