---
title: Vyhodnocení výrazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 423df66e8bd6bc1257a32236aa4ffbb28b80d655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152741"
---
# <a name="expression-evaluator"></a>Vyhodnocovač výrazů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyhodnocovací filtry výrazů (EE) prozkoumají syntaxi jazyka pro analýzu a vyhodnocení proměnných a výrazů za běhu, aby je mohl uživatel zobrazit, když je IDE v režimu pozastavení.  
  
## <a name="using-expression-evaluators"></a>Používání vyhodnocovacích vyhodnocení výrazů  
 Výrazy jsou vytvořeny pomocí metody [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) následujícím způsobem:  
  
1. Ladicí stroj (DE) implementuje rozhraní [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
2. Balíček pro ladění získá `IDebugExpressionContext2` objekt z rozhraní [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) a potom zavolá metodu, `IDebugStackFrame2::ParseText` která získá objekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
3. Balíček ladění volá metodu [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo metodu [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pro získání hodnoty výrazu. `IDebugExpression2::EvaluateAsync` je volána z příkazového nebo příkazového podokna. Všechny ostatní komponenty uživatelského rozhraní volají volání `IDebugExpression2::EvaluateSync` .  
  
4. Výsledek vyhodnocení výrazu je objekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , který obsahuje název, typ a hodnotu výsledku vyhodnocení výrazu.  
  
   Při vyhodnocování výrazu potřebuje EE informace z komponenty poskytovatele symbolů. Zprostředkovatel symbolů poskytuje symbolické informace, které se používají k identifikaci a porozumění analyzovanému výrazu.  
  
   Po dokončení vyhodnocení asynchronního výrazu se pomocí příkazu DE prostřednictvím Správce ladění relace (SDM) pošle asynchronní událost, která upozorní rozhraní IDE na dokončení vyhodnocení výrazu. Po dokončení synchronního vyhodnocení výrazu je výsledek vyhodnocení vrácen z volání `IDebugExpression2::EvaluateSync` metody.  
  
## <a name="implementation-notes"></a>Poznámky k implementaci  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Ladicí stroje očekávají, že mluví s vyhodnocovacím filtrem výrazů pomocí rozhraní CLR (Common Language Runtime). V důsledku toho vyhodnocení výrazu, které funguje s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladicími moduly, musí podporovat modul CLR (úplný seznam všech ladicích rozhraní CLR lze nalézt v debugref.doc, který je součástí [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] ).  
  
## <a name="see-also"></a>Viz také  
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
