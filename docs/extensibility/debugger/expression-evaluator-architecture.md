---
title: Architektura vyhodnocovacího filtru výrazů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738693"
---
# <a name="expression-evaluator-architecture"></a>Architektura vyhodnocovacího filtru výrazů
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Integrace vlastního jazyka do balíčku ladění sady Visual Studio znamená, že je nutné nastavit požadovaná rozhraní vyhodnocovacího filtru výrazů (EE) a volat rozhraní API pro Common Language Runtime symbol Provider (SP) a Binder. Objekty SP a Binder spolu s aktuální adresou spuštění jsou kontext, ve kterém jsou výrazy vyhodnocovány. Informace, které tato rozhraní vyrábí a spotřebovávají, představují klíčové koncepty architektury EE.

## <a name="overview"></a>Přehled

### <a name="parse-the-expression"></a>Analyzovat výraz
 Když ladíte program, výrazy jsou vyhodnocovány z mnoha důvodů, ale vždy, když je program laděn, zastaveno na zarážce (buď zarážku, kterou zadal uživatel nebo je výsledkem výjimka). V tuto chvíli je k dispozici, když Visual Studio získá rámec zásobníku, jak je reprezentované rozhraním [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , z ladicího stroje (de). Visual Studio pak zavolá [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby získalo rozhraní [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Toto rozhraní představuje kontext, ve kterém lze výrazy vyhodnotit; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) je vstupním bodem procesu vyhodnocení. Až do tohoto okamžiku, všechna rozhraní jsou implementována pomocí DE.

 Při `IDebugExpressionContext2::ParseText` volání metody de vytvoří instanci objektu EE přidruženou k jazyku zdrojového souboru, kde došlo k zarážce (de také vytvoří instanci SH v tomto okamžiku). EE je reprezentované rozhraním [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) . Rutina DE then rozvolá [analýzu](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pro převod výrazu (v textovém formátu) na analyzovaný výraz připravený pro vyhodnocení. Tento analyzovaný výraz je reprezentován rozhraním [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) . Výraz je obvykle analyzován a není v tomto okamžiku vyhodnocován.

 DE vytvoří objekt, který implementuje rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , vloží `IDebugParsedExpression` objekt do `IDebugExpression2` objektu a vrátí `IDebugExpression2` objekt z `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>Vyhodnocení výrazu
 Visual Studio volá buď [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , k vyhodnocení analyzovaného výrazu. Obě tyto metody volají [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( `IDebugExpression2::EvaluateSync` volá metodu hned, při `IDebugExpression2::EvaluateAsync` volání metody prostřednictvím vlákna na pozadí) k vyhodnocení analyzovaného výrazu a vrácení rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , které představuje hodnotu a typ analyzovaného výrazu. `IDebugParsedExpression::EvaluateSync` používá poskytnutou SH, adresu a pořadač k převedení analyzovaného výrazu na skutečnou hodnotu reprezentované `IDebugProperty2` rozhraním.

### <a name="for-example"></a>Například
 Po dosažení zarážky v běžícím programu se uživatel rozhodne zobrazit proměnnou v dialogovém okně **QuickWatch** . Toto dialogové okno zobrazuje název proměnné, její hodnotu a její typ. Uživatel může obvykle změnit hodnotu.

 Po zobrazení dialogového okna **QuickWatch** se název zkoušené proměnné pošle jako text do [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Vrátí objekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) představující analyzovaný výraz, v tomto případě proměnnou. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) je poté volána k vyprodukování `IDebugProperty2` objektu, který představuje hodnotu a typ proměnné a také její název. Tyto informace se zobrazí.

 Pokud uživatel změní hodnotu proměnné, je [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) volána s novou hodnotou, která změní hodnotu proměnné v paměti tak, aby se použila při obnovení činnosti programu.

 Další podrobnosti o tomto procesu zobrazení hodnot proměnných naleznete v tématu [zobrazování místních](../../extensibility/debugger/displaying-locals.md) hodnot. Další informace o změně hodnoty proměnné naleznete v tématu [Změna hodnoty místního prostředí](../../extensibility/debugger/changing-the-value-of-a-local.md) .

## <a name="in-this-section"></a>V této části
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md) Poskytuje argumenty, které jsou předány při volání DE v et.

 [Rozhraní vyhodnocovacích výrazů výrazu Key](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Popisuje podklíčová rozhraní potřebná při psaní EE spolu s kontextem vyhodnocení.

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)
- [Změna hodnoty místního](../../extensibility/debugger/changing-the-value-of-a-local.md)
