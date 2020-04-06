---
title: Souvislosti hodnocení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738798"
---
# <a name="evaluation-context"></a>Souvislosti hodnocení
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Když ladicí modul (DE) volá vyhodnocení výrazu (EE), tři argumenty, které jsou předány [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) určit kontext pro hledání a vyhodnocení symbolů, jak je znázorněno v následující tabulce.

## <a name="arguments"></a>Argumenty

|Argument|Popis|
|--------------|-----------------|
|`pSymbolProvider`|Rozhraní [IDebugSymbolProvider,](../../extensibility/debugger/reference/idebugsymbolprovider.md) které určuje obslužnou rutinu symbolu (SH), která má být použita k identifikaci symbolu.|
|`pAddress`|Rozhraní [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) které určuje aktuální bod spuštění. Toto rozhraní vyhledá metodu, která obsahuje spouštěný kód.|
|`pBinder`|[Rozhraní IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) které vyhledá hodnotu a typ symbolu s jeho názvem.|

 `IDebugParsedExpression::EvaluateSync`vrátí rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) představující výslednou hodnotu a její typ.

## <a name="see-also"></a>Viz také
- [Rozhraní hodnotitele klíčových výrazů](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Zobrazení místních obyvatel](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
