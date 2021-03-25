---
description: Toto rozhraní umožňuje správci ladění relace (SDM) načíst rozhraní, které představuje ladicí modul (DE).
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 899c5dceab16d4783cb28bff31c67e67bf5df774
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083645"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Toto rozhraní umožňuje správci ladění relace (SDM) načíst rozhraní, které představuje ladicí modul (DE).

## <a name="syntax"></a>Syntax

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní na objektech, které implementují nejběžnější rozhraní DE (například [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)a [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)), aby bylo umožněno přístupu k rozhraní [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) samotného příkazu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pro získání tohoto rozhraní volejte [QueryInterface](/cpp/atl/queryinterface) pro typické rozhraní de.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugQueryEngine2` .

|Metoda|Popis|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Získá vlastní rozhraní ladicího stroje (DE).|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je obvykle implementováno v objektu, který implementuje rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , aby podporovalo rozkrokování prostřednictvím funkcí; To znamená, že když ladicí program vychází z funkce, další funkce, která má být spuštěna, nemusí být předchozí funkcí v zásobníku, ale funkce v jiném vlákně zcela. Definici "příčiny" naleznete v [glosáři ladicího programu sady Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
