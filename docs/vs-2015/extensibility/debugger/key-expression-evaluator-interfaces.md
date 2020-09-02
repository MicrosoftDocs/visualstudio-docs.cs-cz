---
title: Rozhraní vyhodnocovacích výrazů pro klíčové výrazy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9c01c59e732b777967cf49a61f17305f666325f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805679"
---
# <a name="key-expression-evaluator-interfaces"></a>Rozhraní vyhodnocovače klíčových výrazů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Při psaní vyhodnocovacího filtru výrazů (EE) spolu s testovacím kontextem byste měli být obeznámeni s následujícími rozhraními.  
  
## <a name="interface-descriptions"></a>Popisy rozhraní  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Má jedinou metodu [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), která získá datovou strukturu reprezentující aktuální bod provádění. Tato datová struktura je jedním ze tří argumentů, které ladicí stroj (DE) předá metodě [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) k vyhodnocení výrazu. Toto rozhraní je obvykle implementováno zprostředkovatelem symbolů.  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Má metodu [BIND](../../extensibility/debugger/reference/idebugbinder-bind.md) , která získá oblast paměti obsahující aktuální hodnotu symbolu. V případě, že obsažená metoda reprezentovaná objektem [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) a symbolem, který je reprezentován objektem [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , `IDebugBinder::Bind` vrátí hodnotu symbolu. `IDebugBinder` je obvykle implementováno pomocí DE.  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Představuje jednoduchý datový typ. U složitějších typů, jako jsou pole a metody, použijte odvozená rozhraní [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) a [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) je další důležité odvozené rozhraní, které představuje symboly obsahující jiné symboly, jako jsou metody nebo třídy. `IDebugField`Rozhraní (a jeho deriváty) obvykle implementuje poskytovatel symbolů.  
  
     `IDebugField`Objekt lze použít k vyhledání názvu a typu symbolu a spolu s objektem [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) lze použít k vyhledání jeho hodnoty.  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Představuje skutečné bity hodnoty za běhu symbolu. [BIND](../../extensibility/debugger/reference/idebugbinder-bind.md) převezme objekt [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , který představuje symbol, a vrátí objekt [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) . Metoda [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) vrátí hodnotu symbolu v vyrovnávací paměti. DE obvykle implementuje toto rozhraní, aby představovalo hodnotu vlastnosti v paměti.  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Toto rozhraní představuje samotný vyhodnocovací filtr výrazů. Klíčovou metodou je [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), která vrací rozhraní [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Toto rozhraní představuje analyzovaný výraz připravený k vyhodnocení. Klíčovou metodou je [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , který vrátí IDebugProperty2 reprezentující hodnotu a typ výrazu.  
  
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Toto rozhraní představuje hodnotu a její typ a je výsledkem vyhodnocení výrazu.  
  
## <a name="see-also"></a>Viz také  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)
