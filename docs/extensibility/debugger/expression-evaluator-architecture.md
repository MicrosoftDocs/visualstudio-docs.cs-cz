---
title: Architektura evaluátoru výrazů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738693"
---
# <a name="expression-evaluator-architecture"></a>Architektura vyhodnocení výrazu
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Integrace proprietárního jazyka do balíčku ladění sady Visual Studio znamená, že je nutné nastavit rozhraní vyhodnocení požadovaných výrazů (EE) a volat zprostředkovatele symbolů sp (COMMON Language run-time" a rozhraní pořadače. Sp a pořadač objekty, spolu s aktuální adresu spuštění, jsou kontext, ve kterém jsou vyhodnocovány výrazy. Informace, které tato rozhraní vytvářejí a spotřebovávají představuje klíčové pojmy v architektuře EE.

## <a name="overview"></a>Přehled

### <a name="parse-the-expression"></a>Analyzovat výraz
 Při ladění programu jsou výrazy vyhodnocovány z mnoha důvodů, ale vždy, když byl laděný program zastaven na zarážky (buď zarážka umístěná uživatelem, nebo zarážka způsobená výjimkou). Je v tomto okamžiku, kdy Visual Studio získá rámec zásobníku, reprezentované rozhraní [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) z ladicí modul (DE). Visual Studio pak volá [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) získat rozhraní [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Toto rozhraní představuje kontext, ve kterém lze vyhodnocovat výrazy; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) je vstupním bodem procesu hodnocení. Až do tohoto okamžiku jsou všechna rozhraní implementována DE.

 Při `IDebugExpressionContext2::ParseText` volání DE konkretizovat EE spojené s jazykem zdrojového souboru, kde došlo k zarážky (DE také konkretizovat SH v tomto okamžiku). EE je reprezentován rozhraním [IDebugExpressionEvaluator.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) DE pak volá [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) převést výraz (v textové podobě) na analyzovaný výraz, připravený k vyhodnocení. Tento analyzovaný výraz je reprezentován rozhraním [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md) Výraz je obvykle analyzována a není vyhodnocena v tomto okamžiku.

 DE vytvoří objekt, který implementuje rozhraní [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugParsedExpression` vloží objekt do objektu `IDebugExpression2` a vrátí `IDebugExpression2` objekt z `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Vyhodnocení výrazu
 Visual Studio volá buď [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) vyhodnotit analyzovaný výraz. Obě tyto metody volání`IDebugExpression2::EvaluateSync` [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (volá `IDebugExpression2::EvaluateAsync` metodu okamžitě, zatímco volá metodu prostřednictvím vlákna na pozadí) vyhodnotit analyzovaný výraz a vrátit [rozhraní IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) který představuje hodnotu a typ analyzovaného výrazu. `IDebugParsedExpression::EvaluateSync`Používá zadaný SH, adresu a pořadač k převodu analyzovaného `IDebugProperty2` výrazu na skutečnou hodnotu reprezentovanou rozhraním.

### <a name="for-example"></a>Například
 Po zásahu zarážky v běžícím programu se uživatel rozhodne zobrazit proměnnou v dialogovém okně **Rychlé sledování.** Toto dialogové okno zobrazuje název proměnné, její hodnotu a její typ. Uživatel může obvykle změnit hodnotu.

 Když se zobrazí dialogové okno **Rychlé sledování,** je název zkoumané proměnné odeslán jako text do [programu ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). To vrátí objekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) představující analyzovaný výraz, v tomto případě proměnnou. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) je pak volána k vytvoření objektu, `IDebugProperty2` který představuje hodnotu a typ proměnné, stejně jako její název. Je to informace, která je zobrazena.

 Pokud uživatel změní hodnotu proměnné, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) je volána s novou hodnotu, která změní hodnotu proměnné v paměti, takže bude použita při obnovení programu.

 Další podrobnosti o tomto procesu zobrazení hodnot proměnných naleznete v [tématu Zobrazení místních](../../extensibility/debugger/displaying-locals.md) obyvatel. Další podrobnosti o tom, jak se mění hodnota proměnné, naleznete [v tématu Změna hodnoty místní](../../extensibility/debugger/changing-the-value-of-a-local.md) hod.

## <a name="in-this-section"></a>V tomto oddílu
 [Souvislosti hodnocení](../../extensibility/debugger/evaluation-context.md) Poskytuje argumenty, které jsou předány při volání DE EE.

 [Rozhraní hodnotitele klíčových výrazů](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Popisuje klíčové rozhraní potřebné při psaní EE, spolu s kontextu hodnocení.

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Zobrazení místních obyvatel](../../extensibility/debugger/displaying-locals.md)
- [Změna hodnoty místního](../../extensibility/debugger/changing-the-value-of-a-local.md)
