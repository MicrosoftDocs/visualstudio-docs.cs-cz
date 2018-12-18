---
title: Vyhodnocení výrazu (ladění sady Visual Studio SDK) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52c897e40b825f85e07b4b4f14796655618280a8
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230731"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Vyhodnocení výrazu (Visual Studio ladění SDK)
Během režimu pozastavení rozhraní IDE se musí vyhodnotit jednoduché výrazy zahrnující několik proměnných programu. Ladicí stroj (DE) musí k dosažení hodnocení, analyzovat a vyhodnotit výraz, který se zadá do jedné ze systému windows z integrovaného vývojového prostředí. 
  
 Výrazy se vytvářejí s [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metoda a reprezentována výsledný [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) rozhraní.  
  
 **IDebugExpression2** rozhraní je implementováno DE a volání jeho **EvalAsync** metodu pro návrat [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) rozhraní IDE, aby bylo možné zobrazit výsledky vyhodnocení výrazu v integrovaném vývojovém prostředí. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) vrátí strukturu, která se používá k vložte hodnotu výrazu do **Watch** okno nebo do **lokální** okna.  
  
 Volá ladění balíčku nebo v jiné relaci ladění správci [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) nebo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) získat [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) rozhraní, které představuje Výsledek vyhodnocení. `IDebugProperty2` obsahuje metody, které vrací název, typ a hodnota výrazu. Tyto informace se zobrazí v různých ladicí program systému windows.  
  
## <a name="using-expression-evaluation"></a>Pomocí vyhodnocení výrazu  
 Pokud chcete použít vyhodnocení výrazu, musí implementovat [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metoda a všechny metody [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) rozhraní, jak je znázorněno v následující tabulce.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Vyhodnotí výraz asynchronně.|  
|[Přerušení](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Ukončí asynchronní výraz hodnocení.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Vyhodnotí výraz synchronně.|  
  
 Synchronní a asynchronní vyhodnocování vyžadovat implementaci [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Vyhodnocení výrazu asynchronní vyžaduje implementaci [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvek a stav zkušební spuštění](../../extensibility/debugger/execution-control-and-state-evaluation.md)