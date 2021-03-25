---
title: Vyhodnocení výrazu | Microsoft Docs
description: Přečtěte si o vyhodnocovacích filtrech výrazů, které prozkoumají syntaxi jazyka pro analýzu a vyhodnocení proměnných a výrazů za běhu v režimu pozastavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6876bea4174df7f5ac293ea0d470f5922d7492d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055021"
---
# <a name="expression-evaluator"></a>Vyhodnocení výrazu
Vyhodnocovací filtry výrazů (EE) prozkoumají syntaxi jazyka pro analýzu a vyhodnocení proměnných a výrazů za běhu, aby je mohl uživatel zobrazit, když je IDE v režimu pozastavení.

## <a name="use-expression-evaluators"></a>Použití vyhodnocovacích vyhodnocení výrazů
 Výrazy jsou vytvořeny pomocí metody [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) následujícím způsobem:

1. Ladicí stroj (DE) implementuje rozhraní [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

2. Balíček pro ladění získá `IDebugExpressionContext2` objekt z rozhraní [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) a potom zavolá metodu, `IDebugStackFrame2::ParseText` která získá objekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

3. Balíček ladění volá metodu [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo metodu [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pro získání hodnoty výrazu. `IDebugExpression2::EvaluateAsync` je volána z příkazového nebo příkazového podokna. Všechny ostatní komponenty uživatelského rozhraní volají volání `IDebugExpression2::EvaluateSync` .

4. Výsledek vyhodnocení výrazu je objekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , který obsahuje název, typ a hodnotu výsledku vyhodnocení výrazu.

   Při vyhodnocování výrazu potřebuje EE informace z komponenty poskytovatele symbolů. Zprostředkovatel symbolů poskytuje symbolické informace, které se používají k identifikaci a porozumění analyzovanému výrazu.

   Po dokončení vyhodnocení asynchronního výrazu je pomocí příkazu DE prostřednictvím Správce ladění relace (SDM) odeslána asynchronní událost, která upozorní rozhraní IDE na dokončení vyhodnocení výrazu. A výsledek vyhodnocení se pak vrátí z volání `IDebugExpression2::EvaluateSync` metody.

## <a name="implementation-notes"></a>Poznámky k implementaci
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ladicí stroje očekávají, že mluví s vyhodnocovacím filtrem výrazů pomocí rozhraní CLR (Common Language Runtime). V důsledku toho vyhodnocení výrazu, které funguje s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladicími moduly, musí podporovat modul CLR (úplný seznam všech ladicích rozhraní CLR lze nalézt v debugref.doc, který je součástí [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Viz také
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
