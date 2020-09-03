---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726903"
---
# <a name="idebugmodule2"></a>IDebugModule2
Toto rozhraní představuje modul, tedy spustitelnou jednotku programu, jako je například knihovna DLL.

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, aby představovalo modul a poskytoval přístup k informacím o tomto modulu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání metody [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) vrátí toto rozhraní. DE pošle rozhraní [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) do Správce ladění relace (SDM) pomocí metody [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

 Toto rozhraní lze také vrátit ve struktuře [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (což je vráceno voláním [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Dále](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) vrátí toto rozhraní ([Enummodules –](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) vrátí rozhraní [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) ).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugModule2` .

|Metoda|Popis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Získá [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , který popisuje tento modul.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Zastaralé. NEPOUŽÍVEJTE. Znovu načte symboly pro tento modul.|

## <a name="remarks"></a>Poznámky
 Informace o modulu lze zobrazit v okně **moduly** rozhraní IDE.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
