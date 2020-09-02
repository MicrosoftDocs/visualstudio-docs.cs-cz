---
title: Strategie implementace vyhodnocovacího filtru výrazů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824705"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategie implementace vyhodnocovače výrazů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Jedním z přístupů k rychlému vytváření vyhodnocovacího filtru výrazů (EE) je nejprve implementace minimálního kódu, který je nezbytný k zobrazení místních proměnných v okně **místních** hodnot. Je vhodné si uvědomit, že každý řádek v okně **místní** hodnoty zobrazuje název, typ a hodnotu lokální proměnné a že všechny tři jsou reprezentovány objektem [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Název, typ a hodnotu lokální proměnné lze získat z `IDebugProperty2` objektu voláním metody [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Další informace o zobrazení místních proměnných v okně **místní** hodnoty naleznete v tématu [zobrazení místních](../../extensibility/debugger/displaying-locals.md)hodnot.  
  
## <a name="discussion"></a>Diskuse  
 Možná sekvence implementace začíná implementací [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Metody [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) a [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) je nutné implementovat pro zobrazení místních hodnot. Volání `IDebugExpressionEvaluator::GetMethodProperty` vrátí `IDebugProperty2` objekt, který představuje metodu: to je objekt [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Samotné metody nejsou zobrazeny v okně **místních** hodnot.  
  
 Metoda [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) by měla být implementována jako další. Ladicí stroj (DE) volá tuto metodu, aby získal seznam místních proměnných a argumentů předáním `IDebugProperty2::EnumChildren` `guidFilter` argumentu `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` zavolá [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)a zkombinuje výsledky do jednoho výčtu. Další podrobnosti najdete v tématu [zobrazení místních](../../extensibility/debugger/displaying-locals.md) hodnot.  
  
## <a name="see-also"></a>Viz také  
 [Implementace vyhodnocovacího filtru výrazů](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)
