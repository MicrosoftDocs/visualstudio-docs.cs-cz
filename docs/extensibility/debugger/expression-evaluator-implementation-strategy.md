---
title: Strategie implementace evaluátoru výrazů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738670"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategie implementace vyhodnocení výrazu
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Jedním z přístupů k rychlému vytvoření vyhodnocení výrazu (EE) je nejprve implementovat minimální kód potřebný k zobrazení místních proměnných v okně **Locals.** Je užitečné si uvědomit, že každý řádek v okně **Locals** zobrazuje název, typ a hodnotu místní proměnné a že všechny tři jsou reprezentovány objektem [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) Název, typ a hodnota místní proměnné se `IDebugProperty2` získá z objektu voláním metody [GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Další informace o zobrazení místních proměnných v okně **Locals** naleznete v [tématu Zobrazení místních obyvatel](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Diskuse
 Možná sekvence implementace začíná implementací [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) a [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metody musí být implementovány k zobrazení locals. Volání `IDebugExpressionEvaluator::GetMethodProperty` vrátí `IDebugProperty2` objekt, který představuje metodu: to znamená objekt [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Samotné metody nejsou zobrazeny v okně **Locals.**

 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Metoda by měla být implementována další. Ladicí modul (DE) volá tuto metodu získat seznam místních `IDebugProperty2::EnumChildren` `guidFilter` proměnných `guidFilterLocalsPlusArgs`a argumentů předáním argument . `IDebugProperty2::EnumChildren`volá [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), kombinující výsledky v jednom výčtu. Další podrobnosti [najdete v tématu Zobrazení místních obyvatel.](../../extensibility/debugger/displaying-locals.md)

## <a name="see-also"></a>Viz také
- [Implementace vyhodnocení výrazu](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Zobrazit místní obyvatele](../../extensibility/debugger/displaying-locals.md)
