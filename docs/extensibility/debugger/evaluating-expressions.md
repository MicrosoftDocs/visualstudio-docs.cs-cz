---
title: Vyhodnocení výrazů | Microsoft Docs
description: Přečtěte si o vyhodnocování výrazů, které jsou vytvořeny z řetězců předávaných z automatických, sledovacích, QuickWatch nebo okamžitých oken.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4c79d27c01035f83b506ffad4ec138c8c68f98d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097029"
---
# <a name="evaluate-expressions"></a>Výrazy vyhodnocení
Výrazy jsou vytvořeny z řetězců předaných z **automatických**, **sledovacích**, **QuickWatch** nebo **okamžitých** oken. Při vyhodnocování výrazu vygeneruje tisknutelné řetězec, který obsahuje název a typ proměnné nebo argumentu a jeho hodnotu. Tento řetězec se zobrazí v odpovídajícím okně IDE.

## <a name="implementation"></a>Implementace
 Výrazy jsou vyhodnocovány při zastavení programu na zarážce. Samotný výraz je reprezentován rozhraním [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , které představuje analyzovaný výraz připravený pro vazbu a vyhodnocení v rámci daného kontextu vyhodnocení výrazu. Rámec zásobníku určuje kontext vyhodnocení výrazu, který modul ladění (DE) implementuje implementací rozhraní [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

 V případě uživatelského řetězce a rozhraní [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) může ladicí stroj (de) získat rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) předáním uživatelského řetězce do metody [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . Vrácené rozhraní IDebugExpression2 obsahuje analyzovaný výraz připravený k vyhodnocení.

 Pomocí `IDebugExpression2` rozhraní může de získat hodnotu výrazu prostřednictvím synchronního nebo asynchronního vyhodnocení výrazu pomocí [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Tato hodnota, společně s názvem a typem proměnné nebo argumentu, se pošle na IDE pro zobrazení. Hodnota, název a typ jsou reprezentovány rozhraním [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

 Pro povolení vyhodnocení výrazu DE musí implementovat rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) a [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Synchronní i asynchronní vyhodnocení vyžaduje implementaci metody [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .

## <a name="see-also"></a>Viz také
- [Rámce zásobníku](../../extensibility/debugger/stack-frames.md)
- [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md)
- [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
