---
title: Kontextová | Microsoft Docs
description: 'Když ladicí modul volá vyhodnocovač výrazů, argumenty určují kontext pro vyhledání a vyhodnocení symbolů: pSymbolProvider, pAddress a pBinder.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6c3ab6fe53ad288089dc88587e06547573d80cb9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898575"
---
# <a name="evaluation-context"></a>Kontext vyhodnocení
> [!IMPORTANT]
> V Visual Studio 2015 je tento způsob implementace vyhodnocovače výrazů zastaralý. Informace o implementaci vyhodnocovačů výrazů CLR najdete v tématu Vyhodnocovače [výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovače spravovaných výrazů](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Když ladicí modul (DE) volá vyhodnocovač výrazů (EE), tři argumenty, které jsou předány [evaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) určují kontext pro vyhledání a vyhodnocení symbolů, jak je znázorněno v následující tabulce.

## <a name="arguments"></a>Argumenty

|Argument|Description|
|--------------|-----------------|
|`pSymbolProvider`|Rozhraní [IDebugSymbolProvider,](../../extensibility/debugger/reference/idebugsymbolprovider.md) které určuje obslužnou rutinu symbolů (SH), která se má použít k identifikaci symbolu.|
|`pAddress`|Rozhraní [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) které určuje aktuální bod provádění. Toto rozhraní vyhledá metodu , která obsahuje spuštěný kód.|
|`pBinder`|Rozhraní [IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) které najde hodnotu a typ symbolu s daným názvem.|

 `IDebugParsedExpression::EvaluateSync` vrací [rozhraní IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) představující výslednou hodnotu a její typ.

## <a name="see-also"></a>Viz také
- [Rozhraní vyhodnocovače klíčových výrazů](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Zobrazení místních hodnoty](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
