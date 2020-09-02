---
title: Vyhodnocení výrazu okna kukátka | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f13573cfecbd81f36e3b77e9b23beeaa558c08dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820422"
---
# <a name="evaluating-a-watch-window-expression"></a>Vyhodnocení výrazu okna kukátka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Po pozastavení provádění aplikace Visual Studio zavolá ladicí modul (DE), aby určil aktuální hodnotu každého výrazu v seznamu sledování. DE vyhodnotí každý výraz pomocí vyhodnocení výrazu (EE) a Visual Studio zobrazí jeho hodnotu v okně **kukátko** .  
  
 Tady je přehled toho, jak se vyhodnocuje výraz seznamu sledování:  
  
1. Visual Studio volá [GetExpressionContexta](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) de pro získání kontextu výrazu, který lze použít k vyhodnocení výrazů.  
  
2. Pro každý výraz v seznamu sledování volá Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k převedení textu výrazu na analyzovaný výraz.  
  
3. `IDebugExpressionContext2::ParseText` volá [analýzu](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , aby provede skutečnou práci s analýzou textu a vytvořil objekt [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
4. `IDebugExpressionContext2::ParseText` Vytvoří objekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) a vloží `IDebugParsedExpression` do něj objekt. Tento `DebugExpression2` objekt se pak vrátí do sady Visual Studio.  
  
5. Visual Studio volá [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pro vyhodnocení analyzovaného výrazu.  
  
6. `IDebugExpression2::EvaluateSync` předá volání [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) k provedení skutečného vyhodnocení a vyprodukování objektu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , který je vrácen do sady Visual Studio.  
  
7. Visual Studio volá [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , aby získal hodnotu výrazu, který je pak zobrazen v seznamu sledování.  
  
## <a name="parse-then-evaluate"></a>Analyzovat a pak vyhodnotit  
 Vzhledem k tomu, že analýza složitého výrazu může trvat mnohem déle než vyhodnotit, proces vyhodnocení výrazu je rozdělen do dvou kroků: 1) analýza výrazu a 2) vyhodnocení analyzovaného výrazu. Tímto způsobem může vyhodnocení probíhat mnohokrát, ale výraz musí být analyzován pouze jednou. Mezilehlé analyzovaný výraz je vrácen z bodu EE v objektu [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) , který je zase zapouzdřený a vrácen z objektu de jako objekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpression`Objekt odloží veškeré vyhodnocení `IDebugParsedExpression` objektu.  
  
> [!NOTE]
> Není nutné, aby se v EE dodržoval tento proces se dvěma kroky, i když Visual Studio předpokládá toto. funkce EE může analyzovat a vyhodnocovat ve stejném kroku při volání [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (to znamená, jak funguje ukázka mycee, například). Pokud váš jazyk může tvořit složité výrazy, může být vhodné oddělit krok analýzy od kroku vyhodnocení. To může zvýšit výkon v ladicím programu sady Visual Studio, když je zobrazeno mnoho výrazů kukátka.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ukázková implementace vyhodnocení výrazu](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Používá ukázku MyCEE ke krokování procesu vyhodnocení výrazu.  
  
 [Vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Vysvětluje, co se stane po úspěšné analýze výrazu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)  
 Poskytuje argumenty, které jsou předány, když ladicí stroj (DE) volá vyhodnocovací filtr výrazů (EE).  
  
## <a name="see-also"></a>Viz také  
 [Zápis pro vyhodnocovač výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
