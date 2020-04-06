---
title: IDebugModuleLoadEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2
helpviewer_keywords:
- IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06bb96d8a02ccc9299d43f28b4fbfa3fdb39acdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726697"
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
Toto rozhraní je odesláno ladicí modul (DE) do správce ladění relace (SDM) při načtení nebo uvolnění modulu.

## <a name="syntax"></a>Syntaxe

```
IDebugModuleLoadEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 De implementuje toto rozhraní hlásit, že modul byl načten nebo uvolněn. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události zprávu modul byl načten nebo uvolněn. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm, když je připojen k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce je `IDebugModuleLoadEvent2`uvedena metoda .

|Metoda|Popis|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Získá modul, který je právě načten nebo uvolněn.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá tuto událost k udržení **moduly** okno aktuální.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
