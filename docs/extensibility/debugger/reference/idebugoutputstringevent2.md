---
title: IDebugOutputStringEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726030"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Toto rozhraní je odesláno ladicí modul (DE) do správce ladění relace (SDM) pro výstup řetězce.

## <a name="syntax"></a>Syntaxe

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 De implementuje toto rozhraní k odeslání řetězce do **výstupního** okna rozhraní IDE. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události k odeslání řetězce do okna **Výstup.** Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm, když je připojen k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce je `IDebugOutputStringEvent2`uvedena metoda .

|Metoda|Popis|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Získá zobrazitelnou zprávu.|

## <a name="remarks"></a>Poznámky
 Například v nespravovaném kódu může řetězec, který má být výstup, originate, když `OutputDebugString` laděný program odešle řetězec do funkce Win32. Tento řetězec je zachycen DE a odeslány na SDM jako `IDebugOutputStringEvent2` událost.

 Pomocí [protokolu IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) odešlete zprávu, která vyžaduje odpověď uživatele.

 Pomocí [aplikace IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) odešlete chybovou zprávu, která nevyžaduje odpověď.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
