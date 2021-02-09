---
title: Vyhodnocení výrazu (Visual Studio Debugging SDK) | Microsoft Docs
description: Během režimu přerušení rozhraní IDE vyhodnocuje výrazy zahrnující proměnné programu. Přečtěte si, jak ladicí stroj analyzuje a vyhodnocuje výraz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 772d38b328eca1e0afb6ff48a5ad580d01939527
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921478"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Vyhodnocení výrazu (sada SDK pro ladění sady Visual Studio)
Během režimu přerušení musí IDE vyhodnotit jednoduché výrazy, které obsahují několik proměnných programu. Aby bylo možné provést vyhodnocení, musí modul ladění (DE) analyzovat a vyhodnocovat výraz, který je zadán v jednom z oken rozhraní IDE.

 Výrazy jsou vytvořeny pomocí metody [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) a reprezentované výsledným rozhraním [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

 Rozhraní **IDebugExpression2** je implementováno pomocí příkazu de a volá jeho metodu **EvalAsync** pro návrat rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) do prostředí IDE, aby bylo možné zobrazit výsledky vyhodnocení výrazu v integrovaném vývojovém prostředí (IDE). [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) vrátí strukturu, která se používá k vložení hodnoty výrazu do okna **kukátka** nebo do okna **místních** hodnot.

 Balíček ladění nebo správce ladění relace (SDM) volá [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) nebo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pro získání rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , které představuje výsledek vyhodnocení. `IDebugProperty2` má metody, které vracejí název, typ a hodnotu výrazu. Tyto informace se zobrazí v různých oknech ladicího programu.

## <a name="using-expression-evaluation"></a>Použití vyhodnocení výrazu
 Chcete-li použít vyhodnocení výrazu, je nutné implementovat metodu [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) a všechny metody rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , jak je znázorněno v následující tabulce.

|Metoda|Popis|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Vyhodnotí výraz asynchronně.|
|[Přerušit](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Ukončí vyhodnocení asynchronního výrazu.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Vyhodnotí výraz synchronně.|

 Synchronní a asynchronní vyhodnocení vyžaduje implementaci metody [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Vyhodnocení asynchronního výrazu vyžaduje implementaci [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
