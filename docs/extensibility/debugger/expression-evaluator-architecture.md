---
title: Architektura vyhodnocovače výrazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5110b34c13952e359b494352063a2a277fbdcdde
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232033"
---
# <a name="expression-evaluator-architecture"></a>Architektura vyhodnocovače výrazů
> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka Chyba při vyhodnocování výrazu spravované](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Integrace proprietární jazyk do sady Visual Studio ladit balíček znamená, že musíte nastavit rozhraní vyhodnocovače (EE) vyžaduje výraz a volání běžné poskytovatele jazykového nastavení symbolu za běhu (SP) a rozhraní vazače. SP a vazače objekty, spolu s aktuální adresou spuštění jsou kontext, ve kterém jsou výrazy vyhodnocovány. Informace, které tato rozhraní produkovat a konzumovat představuje klíčových konceptů v architektuře EE.  
  
## <a name="overview"></a>Přehled  
  
### <a name="parse-the-expression"></a>Parsování výrazu  
 Při ladění programu, jsou výrazy vyhodnocovány pro několik důvodů, ale vždy když laděný program se zastavil na zarážce (zarážku umístěn uživatelem nebo jeden způsobené výjimku). V tomto okamžiku, kdy sady Visual Studio získá rámec zásobníku, je reprezentovaná [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) rozhraní z ladicího stroje (DE). Visual Studio pak zavolá [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zobrazíte [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) rozhraní. Toto rozhraní představuje kontext, ve kterém můžete vyhodnotit výrazy; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) je vstupním bodem k hodnocení. Do této chvíle jsou všechna rozhraní implementované DE.  
  
 Když `IDebugExpressionContext2::ParseText` je volána, DE vytvoří instanci EE přidružený jazyk zdrojového souboru, kde došlo k zarážce (DE také vytvoří instanci SH v tuto chvíli). Je reprezentován EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) rozhraní. Pak zavolá DE [analyzovat](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) převést na výraz analyzovaný výrazu (ve formě textu), připraveno pro hodnocení. Tato analyzovaný výraz je reprezentován [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) rozhraní. Výraz je obvykle analyzovat a není v tuto chvíli vyhodnotit.  
  
 DE vytvoří objekt, který implementuje [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) rozhraní, vloží `IDebugParsedExpression` objektu do `IDebugExpression2` objekt a vrátí `IDebugExpression2` objektu z `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluate-the-expression"></a>Vyhodnocení výrazu  
 Visual Studio vyžaduje buď [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) analyzovaný vyhodnotit. Obě tyto metody volat [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` volá metodu okamžitě, zatímco `IDebugExpression2::EvaluateAsync` volá metodu prostřednictvím vlákna na pozadí) analyzovaný vyhodnotit a vrátíte se [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) rozhraní, které představuje hodnotu a typ analyzovaný výrazu. `IDebugParsedExpression::EvaluateSync` používá zadaný SH, adresu a vazače převést analyzovaný výraz na skutečnou hodnotu, reprezentovaný `IDebugProperty2` rozhraní.  
  
### <a name="for-example"></a>Příklad  
 Po dosažení zarážky v běžící aplikaci uživatel zvolí možnost zobrazit proměnnou **QuickWatch** dialogové okno. Toto dialogové okno zobrazí název proměnné, jeho hodnota a její typ. Uživatel může změnit obvykle hodnota.  
  
 Když **QuickWatch** se zobrazí dialogové okno, název proměnné zkoumají odeslán jako text, který má [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Tím se vrátí [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objekt v tomto případě představující analyzovaný výrazu, proměnné. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) potom je volána k vytvoření `IDebugProperty2` objekt, který reprezentuje hodnotu proměnné a typ, jakož i její název. Je tato informace, které se zobrazí.  
  
 Pokud uživatel změní hodnotu proměnné [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) volána s novou hodnotu, která změní hodnotu proměnné v paměti, použije se po obnovení program spuštěn.  
  
 Zobrazit [zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md) podrobné informace o tomto procesu zobrazení hodnot proměnných. Zobrazit [změna hodnoty lokální](../../extensibility/debugger/changing-the-value-of-a-local.md) podrobné informace o tom, jak se změní hodnota proměnné.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)  
 Obsahuje argumenty, které se předávají při DE volání EE.  
  
 [Rozhraní vyhodnocovače klíčových výrazů](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Popisuje klíčové rozhraní potřebné při zápisu EE, spolu s kontext vyhodnocení.  
  
## <a name="see-also"></a>Viz také:  
 [Zápis vyhodnocovací filtr výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)   
 [Změna hodnoty lokální](../../extensibility/debugger/changing-the-value-of-a-local.md)