---
title: Vyhodnocení výrazu (Sada Visual Studio ladění sady SDK) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738713"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Vyhodnocení výrazu (Visual Studio ladění SDK)
Během režimu přerušení ide musí vyhodnotit jednoduché výrazy zahrnující několik proměnných programu. Chcete-li provést jeho vyhodnocení, ladicí modul (DE) musí analyzovat a vyhodnotit výraz, který je zadán do jednoho z oken ide.

 Výrazy jsou vytvořeny pomocí metody [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) a reprezentovány výsledným rozhraním [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

 **Rozhraní IDebugExpression2** je implementováno DE a volá jeho **EvalAsync** metoda vrátit rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) do IDE, aby se zobrazily výsledky vyhodnocení výrazu v ide. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) vrátí strukturu, která se používá k vložíní hodnotu výrazu do okna **Watch** nebo do okna **Locals.**

 Ladicí balíček nebo správce ladění relace (SDM) volá [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) nebo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) získat rozhraní [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) které představuje výsledek vyhodnocení. `IDebugProperty2`má metody, které vracejí název, typ a hodnotu výrazu. Tyto informace se zobrazí v různých oknech ladicího programu.

## <a name="using-expression-evaluation"></a>Použití vyhodnocení výrazu
 Chcete-li použít vyhodnocení výrazu, musíte implementovat metodu [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) a všechny metody rozhraní [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) jak je znázorněno v následující tabulce.

|Metoda|Popis|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Vyhodnotí výraz asynchronně.|
|[Přerušení](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Ukončí vyhodnocení asynchronního výrazu.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Vyhodnotí výraz synchronně.|

 Synchronní a asynchronní vyhodnocení vyžaduje implementaci metody [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Vyhodnocení asynchronního výrazu vyžaduje implementaci [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
