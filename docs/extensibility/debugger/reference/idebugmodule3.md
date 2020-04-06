---
title: IDebugModule3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726741"
---
# <a name="idebugmodule3"></a>IDebugModule3
Toto rozhraní představuje modul, který podporuje alternativní umístění symbolů a JustMyCode státy.

## <a name="syntax"></a>Syntaxe

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní pro podporu alternativní umístění symbolů a pro práci se stavy JustMyCode (viz [Glosář ladicího programu Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) pro definici "JustMyCode").

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) vrátí toto rozhraní. De odešle rozhraní [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) do správce ladění relace (SDM) pomocí [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody. Také volání [QueryInterface](/cpp/atl/queryinterface) v rozhraní [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod v rozhraní [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Vrátí seznam cest prohledávaných symbolů a výsledky hledání jednotlivých cest.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Načte a inicializuje symboly pro aktuální modul.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Vrátí příznak určující, zda modul představuje uživatelský kód.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Určuje, zda má být modul považován za uživatelský kód nebo ne.|

## <a name="remarks"></a>Poznámky
 Visual Studio je typickým příjemcem tohoto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
