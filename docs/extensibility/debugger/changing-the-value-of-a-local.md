---
title: Změna hodnoty místní | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739147"
---
# <a name="change-the-value-of-a-local"></a>Změna hodnoty místního
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Když je zadána nová hodnota do pole hodnoty **locals** okna, ladicí balíček předá řetězec, jak je napsáno, vyhodnocení výrazu (EE). EE vyhodnotí tento řetězec, který může obsahovat jednoduchou hodnotu nebo výraz a uloží výslednou hodnotu do přidruženého místního.

 Toto je přehled procesu změny hodnoty místního:

1. Poté, co uživatel zadá novou hodnotu, Visual Studio volá [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) na [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objekt přidružený k místní.

2. `IDebugProperty2::SetValueAsString` provede následující úlohy:

   1. Vyhodnotí řetězec k vytvoření hodnoty.

   2. Váže přidružený objekt [IDebugField](../../extensibility/debugger/reference/idebugfield.md) a získá objekt [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md)

   3. Převede hodnotu na řadu bajtů.

   4. Volání [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) umístit bajtů hodnoty do paměti, takže program, který je laděný přístup k nim.

3. Visual Studio aktualizuje **místní** zobrazení (viz [Zobrazení místních podrobností).](../../extensibility/debugger/displaying-locals.md)

   Tento postup se také používá ke změně hodnoty proměnné v okně `IDebugProperty2` **Watch,** s tím rozdílem, že se jedná o objekt přidružený k hodnotě local, který se používá namísto objektu `IDebugProperty2` přidruženého k samotnému místnímu objektu.

## <a name="in-this-section"></a>V tomto oddílu
 [Ukázková implementace měnících se hodnot](../../extensibility/debugger/sample-implementation-of-changing-values.md) Používá mycee ukázku krokovat proces změny hodnot.

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Zobrazení místních obyvatel](../../extensibility/debugger/displaying-locals.md)
