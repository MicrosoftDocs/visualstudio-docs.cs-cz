---
title: Strategie implementace vyhodnocovacího filtru výrazů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738670"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategie implementace vyhodnocovacího filtru výrazů
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Jedním z přístupů k rychlému vytváření vyhodnocovacího filtru výrazů (EE) je nejprve implementace minimálního kódu, který je nezbytný k zobrazení místních proměnných v okně **místních** hodnot. Je vhodné si uvědomit, že každý řádek v okně **místní** hodnoty zobrazuje název, typ a hodnotu lokální proměnné a že všechny tři jsou reprezentovány objektem [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Název, typ a hodnotu lokální proměnné jsou získány z `IDebugProperty2` objektu voláním metody [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Další informace o zobrazení místních proměnných v okně **místní** hodnoty naleznete v tématu [zobrazení místních](../../extensibility/debugger/displaying-locals.md)hodnot.

## <a name="discussion"></a>Diskuse
 Možná sekvence implementace začíná implementací [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Metody [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) a [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) musí být implementovány pro zobrazení místních hodnot. Volání `IDebugExpressionEvaluator::GetMethodProperty` vrátí `IDebugProperty2` objekt, který představuje metodu: to je objekt [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Samotné metody nejsou zobrazeny v okně **místních** hodnot.

 Metoda [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) by měla být implementována jako další. Ladicí stroj (DE) volá tuto metodu, aby získal seznam místních proměnných a argumentů předáním `IDebugProperty2::EnumChildren` `guidFilter` argumentu `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` zavolá [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)a zkombinuje výsledky do jednoho výčtu. Další podrobnosti najdete v tématu [zobrazení místních](../../extensibility/debugger/displaying-locals.md) hodnot.

## <a name="see-also"></a>Viz také
- [Implementace vyhodnocovacího filtru výrazů](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Zobrazit místní hodnoty](../../extensibility/debugger/displaying-locals.md)
