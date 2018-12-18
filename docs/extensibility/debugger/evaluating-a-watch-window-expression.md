---
title: Vyhodnocení výrazu okna kukátka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47e875f4d288c896ace377e2844192aa5c3be275
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232100"
---
# <a name="evaluate-a-watch-window-expression"></a>Vyhodnocení výrazu okna kukátka
> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka Chyba při vyhodnocování výrazu spravované](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Při pozastavení provádění volání sady Visual Studio ladicího stroje (DE) Chcete-li zjistit aktuální hodnotu každý výraz v svůj seznam ke zhlédnutí. DE vyhodnocuje každý výraz pomocí vyhodnocovače výrazů (EE) a Visual Studio zobrazí její hodnotu v **Watch** okna.  
  
 Tady je přehled způsob vyhodnocení výrazu kukátka seznamu:  
  
1.  Volání sady Visual Studio je DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) získat výraz kontext, který lze použít k vyhodnocení výrazů.  
  
2.  Pro každý výraz v seznamu sledování volání sady Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) převést na výraz analyzovaného textu výrazu.  
  
3.  `IDebugExpressionContext2::ParseText` volání [analyzovat](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) k vykonávají samotnou práci při analýze textu a produktů [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objektu.  
  
4.  `IDebugExpressionContext2::ParseText` vytvoří [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objektu a vloží `IDebugParsedExpression` objektu do něj. Tato můžu`DebugExpression2` objekt je pak vrácen do sady Visual Studio.  
  
5.  Visual Studio volání [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) analyzovaný vyhodnotit.  
  
6.  `IDebugExpression2::EvaluateSync` předává volání [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) skutečné hodnocení a vytvářet [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objekt, který je vrácen do sady Visual Studio.  
  
7.  Visual Studio volání [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) k získání hodnoty výraz, který se následně zobrazí v seznamu sledování.  
  
## <a name="parse-then-evaluate"></a>Analyzovat a vyhodnocení  
 Protože parsování složitý výraz může trvat déle než vyhodnocení, proces vyhodnocení výrazu je rozdělený do dvou kroků: 1) parsovat výraz a (2) analyzovaný výraz vyhodnotit. Tímto způsobem vyhodnocení může dojít v mnoha případech ale výraz musí být pouze jednou analyzována. Zprostředkující analyzovaný výraz vrátí EE v [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objekt, který je pak zapouzdřen a byla vrácena z DE jako [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objektu. `IDebugExpression` Objekt odloží všechny vyhodnocení `IDebugParsedExpression` objektu.  
  
> [!NOTE]
>  Není nutné pro EE dodržovat tento dvoukrokový proces i v případě, že to; předpokládá Visual Studio EE můžete analyzovat a vyhodnotit do jednoho kroku při [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) nazývá (Toto je ukázka MyCEE fungování, třeba). Pokud váš jazyk mohl vytvořit složité výrazy, můžete chtít oddělit krok analýzy z kroku hodnocení. To může zvýšit výkon v ladicím programu sady Visual Studio, když mnoho sledovat výrazy se zobrazují.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ukázková implementace vyhodnocení výrazu](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Používá ukázkový MyCEE pro jednotlivé kroky v procesu vyhodnocení výrazu.  
  
 [Vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Vysvětluje, co se stane po úspěšné výraz analýzy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)  
 Poskytuje argumenty předávané při volání ladicího stroje (DE) vyhodnocovací filtr výrazů (EE).  
  
## <a name="see-also"></a>Viz také:  
 [Zápis vyhodnocovací filtr výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)