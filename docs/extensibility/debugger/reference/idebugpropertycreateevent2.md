---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 08ef46275d9c7365cfcc837b8e4dfc73f0b48b41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876053"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Toto rozhraní se odesílá ladicím modulem (DE) do Správce ladění relace (SDM), když vytvoří vlastnost, která je přidružena k určitému dokumentu.

## <a name="syntax"></a>Syntax

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo, že byla vytvořena vlastnost. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` . Toto rozhraní je implementováno, pokud DE vytvořila vlastnost přidruženou ke skriptu, který byl načten nebo vytvořen a v případě, že se tento skript musí objevit v integrovaném vývojovém prostředí.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Vlastnost DE vytvoří a pošle tento objekt události k vytvoření sestavy vlastnosti. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojená k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Následující tabulka ukazuje metodu `IDebugPropertyCreateEvent2` rozhraní.

|Metoda|Popis|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Získá novou vlastnost.|

## <a name="remarks"></a>Poznámky
 Pokud má vlastnost k ní přidružený konkrétní dokument nebo skript, může DE odeslat tuto událost do SDM, aby aktualizovala okno **dokumenty skriptu** s názvem dokumentu. Model SDM bude volat [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) s argumentem `guidDocument` pro načtení `VARIANT` obsahujícího ukazatele [IUnknown](/cpp/atl/iunknown) . Model SDM zavolá [QueryInterface](/cpp/atl/queryinterface) na tento ukazatel, aby získal rozhraní [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , které se používá k aktualizaci okna **dokumenty skriptu** .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
