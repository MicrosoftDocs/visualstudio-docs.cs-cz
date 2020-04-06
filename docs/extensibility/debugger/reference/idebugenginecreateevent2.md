---
title: IDebugEngineCreateEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a964f1e08fc2e88ac9a1d211e4b3e36b32c5b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730599"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
Ladicí modul (DE) odešle toto rozhraní správci ladění relace (SDM) při vytvoření instance DE.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní jako součást své běžné operace. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako `QueryInterface` toto `IDebugEvent2` rozhraní (SDM používá metodu pro přístup k rozhraní).

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události po DE byla vytvořena instance. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm při připojení k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugEngineCreateEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Načte objekt, který představuje nově vytvořený ladicí modul (DE).|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
