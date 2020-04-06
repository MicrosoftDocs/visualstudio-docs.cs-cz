---
title: Hodnocení výrazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738826"
---
# <a name="evaluate-expressions"></a>Vyhodnocení výrazů
Výrazy jsou vytvářeny z řetězců předávacích z oken **Autos**, **Watch**, **QuickWatch**nebo **Immediate.** Při vyhodnocení výrazu generuje tisknutelný řetězec, který obsahuje název a typ proměnné nebo argumentu a jeho hodnotu. Tento řetězec se zobrazí v odpovídajícím okně IDE.

## <a name="implementation"></a>Implementace
 Výrazy jsou vyhodnocovány, když se program zastavil na zarážky. Samotný výraz je reprezentován rozhraním [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) které představuje analyzovaný výraz, který je připraven pro vazbu a vyhodnocení v rámci kontextu vyhodnocení daného výrazu. Rámec zásobníku určuje kontext vyhodnocení výrazu, který poskytuje ladicí modul (DE) implementací rozhraní [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

 Vzhledem k tomu, uživatelský řetězec a [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) rozhraní, ladicí modul (DE) můžete získat rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) předáním uživatelského řetězce [iDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metoda. Rozhraní IDebugExpression2, které je vráceno obsahuje analyzovaný výraz připravený k vyhodnocení.

 S `IDebugExpression2` rozhraním de může získat hodnotu výrazu prostřednictvím synchronní nebo asynchronní vyhodnocení výrazu pomocí [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Tato hodnota spolu s názvem a typem proměnné nebo argumentu je odeslána do ide pro zobrazení. Hodnota, název a typ jsou reprezentovány rozhraním [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

 Chcete-li povolit vyhodnocení výrazu, de musí implementovat [rozhraní IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) a [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Synchronní i asynchronní vyhodnocení vyžaduje implementaci metody [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

## <a name="see-also"></a>Viz také
- [Stohovat rámce](../../extensibility/debugger/stack-frames.md)
- [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md)
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
