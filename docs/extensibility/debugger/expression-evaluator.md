---
title: Evaluátor výrazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738686"
---
# <a name="expression-evaluator"></a>Vyhodnocení výrazu
Vyhodnocení výrazů (EE) prozkoumat syntaxi jazyka analyzovat a vyhodnotit proměnné a výrazy za běhu, což umožňuje jejich zobrazení uživatelem, když je rozhraní IDE v režimu přerušení.

## <a name="use-expression-evaluators"></a>Použití vyhodnocení výrazů
 Výrazy jsou vytvářeny pomocí metody [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) následujícím způsobem:

1. Ladicí modul (DE) implementuje rozhraní [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. Balíček ladění získá `IDebugExpressionContext2` objekt z rozhraní [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) `IDebugStackFrame2::ParseText` a potom volá metodu na něm získat objekt [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

3. Balíček ladění volá [metodu EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo metodu [EvaluateAsync,](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) aby získal hodnotu výrazu. `IDebugExpression2::EvaluateAsync`je volána z okna Příkaz/Okamžité. Volání všech ostatních `IDebugExpression2::EvaluateSync`součástí ui .

4. Výsledkem vyhodnocení výrazu je objekt [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) který obsahuje název, typ a hodnotu výsledku vyhodnocení výrazu.

   Během vyhodnocení výrazu EE vyžaduje informace z komponenty zprostředkovatele symbolů. Poskytovatel symbolu poskytuje symbolické informace používané pro identifikaci a pochopení analyzovaného výrazu.

   Po dokončení vyhodnocení asynchronního výrazu je asynchronní událost odeslána de prostřednictvím správce ladění relace (SDM) upozornit ide, že vyhodnocení výrazu je dokončena. A výsledek hodnocení je pak vrácena z `IDebugExpression2::EvaluateSync` volání metody.

## <a name="implementation-notes"></a>Poznámky k implementaci
 Ladicí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moduly očekávají, že mluvit s vyhodnocení výrazu pomocí common language runtime (CLR) rozhraní. V důsledku toho vyhodnocení výrazu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] který pracuje s ladicími moduly musí podporovat CLR (úplný seznam všech rozhraní ladění CLR lze [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]nalézt v debugref.doc, který je součástí ).

## <a name="see-also"></a>Viz také
- [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md)
