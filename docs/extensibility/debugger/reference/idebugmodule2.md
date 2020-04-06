---
title: IDebugModule2 | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726903"
---
# <a name="idebugmodule2"></a>IDebugModule2
Toto rozhraní představuje modul – to znamená spustitelnou jednotku programu – například knihovnu DLL.

## <a name="syntax"></a>Syntaxe

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující modul a poskytnout přístup k informacím o tomto modulu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) vrátí toto rozhraní. De odešle rozhraní [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) do správce ladění relace (SDM) pomocí [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.

 Toto rozhraní lze také vrátit ve struktuře [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (která je vrácena voláním [EnumFrameInfo).](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

- [Další](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) také vrátí toto rozhraní ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) vrátí rozhraní [IEnumDebugModules2).](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugModule2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Získá [MODULE_INFO,](../../../extensibility/debugger/reference/module-info.md) který popisuje tento modul.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Zastaralé. NEPOUŽÍVEJTE. Znovu načte symboly pro tento modul.|

## <a name="remarks"></a>Poznámky
 Informace o modulu lze zobrazit v okně **Moduly** ide.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
