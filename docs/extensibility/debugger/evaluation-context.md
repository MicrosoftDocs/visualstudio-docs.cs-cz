---
title: Kontext vyhodnocení | Microsoft Docs
description: 'Když ladicí stroj volá vyhodnocovací filtr výrazů, argumenty určují kontext pro hledání a vyhodnocení symbolů: pSymbolProvider, pAddress a pBinder.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0957a204a83ab72aabe14fe4a70d8e758e83a08f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840584"
---
# <a name="evaluation-context"></a>Kontext vyhodnocení
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Když ladicí stroj (DE) volá vyhodnocovací filtr výrazů (EE), tři argumenty předané do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) určují kontext pro hledání a vyhodnocení symbolů, jak je znázorněno v následující tabulce.

## <a name="arguments"></a>Argumenty

|Argument|Description|
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
