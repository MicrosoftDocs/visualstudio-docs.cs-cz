---
title: IDebugPropertyCreateEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720927"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Toto rozhraní je odesláno ladicí modul (DE) do správce ladění relace (SDM) při vytvoření vlastnosti, která je přidružena k určitému dokumentu.

## <a name="syntax"></a>Syntaxe

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní hlásit, že byla vytvořena vlastnost. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní. Toto rozhraní je implementováno, pokud DE vytvořil vlastnost přidruženou ke skriptu, který byl načten nebo vytvořen, a pokud se tento skript musí zobrazit v rozhraní IDE.

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události zprávu vlastnost byla vytvořena. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm, když je připojen k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce je `IDebugPropertyCreateEvent2` uvedena metoda rozhraní.

|Metoda|Popis|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Získá novou vlastnost.|

## <a name="remarks"></a>Poznámky
 Pokud má vlastnost přidružený určitý dokument nebo skript, může DE odeslat tuto událost do programu SDM za účelem aktualizace okna **Skriptovat dokumenty** s názvem dokumentu. SDM bude volat [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) `guidDocument` s argumentem `VARIANT` načíst obsahující [ukazatel IUnknown.](/cpp/atl/iunknown) SDM bude volat [QueryInterface](/cpp/atl/queryinterface) na tento ukazatel načíst rozhraní [IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) který se používá k aktualizaci okna **Dokumenty skriptu.**

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
