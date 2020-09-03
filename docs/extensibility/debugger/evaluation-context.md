---
title: Kontext vyhodnocení | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738798"
---
# <a name="evaluation-context"></a>Kontext vyhodnocení
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Když ladicí stroj (DE) volá vyhodnocovací filtr výrazů (EE), tři argumenty předané do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) určují kontext pro hledání a vyhodnocení symbolů, jak je znázorněno v následující tabulce.

## <a name="arguments"></a>Arguments

|Argument|Popis|
|--------------|-----------------|
|`pSymbolProvider`|Rozhraní [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) , které určuje obslužnou rutinu symbolu (SH), která se má použít k identifikaci symbolu.|
|`pAddress`|Rozhraní [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , které určuje aktuální bod provádění. Toto rozhraní najde metodu, která obsahuje prováděný kód.|
|`pBinder`|Rozhraní [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) , které najde hodnotu a typ symbolu daného názvu.|

 `IDebugParsedExpression::EvaluateSync` Vrátí rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) představující výslednou hodnotu a její typ.

## <a name="see-also"></a>Viz také
- [Rozhraní vyhodnocovacích výrazů výrazu Key](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
