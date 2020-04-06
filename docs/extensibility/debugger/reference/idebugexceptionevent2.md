---
title: IDebugExceptionEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729776"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Ladicí modul (DE) odešle toto rozhraní správci ladění relace (SDM), když je vyvolána výjimka v aktuálně prováděném programu.

## <a name="syntax"></a>Syntaxe

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 De implementuje toto rozhraní hlásit, že došlo k výjimce v programu, který je laděn. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události hlásit výjimku. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm při připojení k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugExceptionEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Získá podrobné informace o výjimce, která byla aktivována tuto událost.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Získá popis čitelný pro vyvolána výjimka, která byla aktivována tuto událost.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Určuje, zda ladicí modul (DE) podporuje možnost předání této výjimky programu, který je laděn při obnovení provádění.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Určuje, zda má být výjimka předána programu, který je laděn při obnovení provádění, nebo zda má být výjimka zahozena.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Poznámky
 Před odesláním události DE zkontroluje, zda tato událost výjimky byla označena jako výjimka první šance nebo druhá šance předchozím voláním [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Pokud byla určena jako výjimka první šance, `IDebugExceptionEvent2` událost je odeslána do SDM. Pokud tomu tak není, DE dává aplikaci možnost zpracovat výjimku. Pokud není k dispozici obslužná rutina výjimky a pokud `IDebugExceptionEvent2` byla výjimka označena jako výjimka druhé šance, je událost odeslána do sdm. V opačném případě DE obnoví provádění programu a operační systém nebo runtime zpracovává výjimku.

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
