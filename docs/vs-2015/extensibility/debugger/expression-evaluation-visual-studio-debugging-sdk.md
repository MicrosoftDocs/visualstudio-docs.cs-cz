---
title: Vyhodnocení výrazu (ladění sady Visual Studio SDK) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb5bfe5f5c77e7ba1881f803830e1cb3d357561b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781579"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Vyhodnocení výrazu (sada SDK pro ladění sady Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Během režimu pozastavení musí být schopen vyhodnotit jednoduché výrazy zahrnující několik proměnných programu integrovaného vývojového prostředí. K tomu ladicího stroje (DE) musí být schopen analyzovat a vyhodnotit výraz, který se zadá do jedné ze systému windows z integrovaného vývojového prostředí.  
  
 Výrazy se vytvářejí pomocí [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metoda a jsou reprezentovány výsledný [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) rozhraní.  
  
 **IDebugExpression2** rozhraní je implementováno DE a volání jeho **EvalAsync** metodu pro návrat [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) rozhraní IDE, aby bylo možné zobrazit výsledky vyhodnocení výrazu v integrovaném vývojovém prostředí. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) vrátí strukturu, která je možné vložit hodnotu výrazu do okna kukátka nebo v okně místních hodnot.  
  
 Volá ladění balíčku nebo v jiné relaci ladění správci [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) nebo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) získat [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) rozhraní, které představuje Výsledek vyhodnocení. `IDebugProperty2` obsahuje metody, které vrací název, typ a hodnota výrazu. Tyto informace se zobrazují v různých ladicí program systému windows.  
  
## <a name="using-expression-evaluation"></a>Pomocí vyhodnocení výrazu  
 Pokud chcete použít vyhodnocení výrazu, musí implementovat [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metoda a všechny metody [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) rozhraní, jak je znázorněno v následující tabulce.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Vyhodnotí výraz asynchronně.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Ukončí asynchronní výraz hodnocení.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Vyhodnotí výraz synchronně.|  
  
 Synchronní a asynchronní vyhodnocování vyžadují provádění [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Vyhodnocení výrazu asynchronní vyžaduje implementaci [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)

