---
title: IDebugQueryEngine2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720650"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Toto rozhraní umožňuje správce ladění relace (SDM) načíst rozhraní, které představuje ladicí modul (DE).

## <a name="syntax"></a>Syntaxe

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní na objekty, které implementují nejběžnější DE rozhraní (například [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)a [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) s cílem umožnit přístup k rozhraní [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) de sám.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [QueryInterface](/cpp/atl/queryinterface) na typické rozhraní DE získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugQueryEngine2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Získá rozhraní vlastního ladicího modulu (DE).|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je obvykle implementováno v objektu, který implementuje rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) za účelem podpory krokování seřazené příčinné souvislosti funkce; to znamená, že když ladicí program odstupuje z funkce, další funkce, která má být spuštěna, nemusí být předchozí funkce v zásobníku, ale funkce v jiném vlákně úplně. Definici "příčinné souvislosti" naleznete v [glosáři ladicího programu sady Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
