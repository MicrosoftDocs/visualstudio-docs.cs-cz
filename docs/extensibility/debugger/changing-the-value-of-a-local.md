---
title: Změna hodnoty místního | Microsoft Docs
description: Přečtěte si o procesu změny hodnoty místních při zadání nové hodnoty v poli hodnota v okně místní hodnoty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08f366162f4031b9cc7aa651bf9eca7aab55a15a
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914332"
---
# <a name="change-the-value-of-a-local"></a>Změna hodnoty místní
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Když je v poli hodnota v okně **místní** hodnoty zadána nová hodnota, ladicí balíček předá do vyhodnocovacího výrazu (EE) řetězec jako zadaný. EE vyhodnocuje tento řetězec, který může obsahovat jednoduchou hodnotu nebo výraz a ukládá výslednou hodnotu do přidružené místní.

 Toto je přehled procesu změny hodnoty místního:

1. Poté, co uživatel zadá novou hodnotu, Visual Studio zavolá [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) na objekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) přidružený k místnímu.

2. `IDebugProperty2::SetValueAsString` provede následující úlohy:

   1. Vyhodnotí řetězec pro vytvoření hodnoty.

   2. Váže přidružený objekt [IDebugField](../../extensibility/debugger/reference/idebugfield.md) k získání objektu [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) .

   3. Převede hodnotu na řadu bajtů.

   4. Volá metodu [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) pro vložení bajtů hodnoty do paměti, aby k nim mohl program ladit přístup.

3. Visual Studio aktualizuje zobrazení **místních** hodnot (podrobnosti najdete v tématu [zobrazování místních](../../extensibility/debugger/displaying-locals.md) hodnot).

   Tento postup se používá také ke změně hodnoty proměnné v okně **kukátko** , s tím rozdílem, že se jedná o `IDebugProperty2` objekt přidružený k hodnotě místního, která je použita místo `IDebugProperty2` objektu přidruženého k místnímu objektu.

## <a name="in-this-section"></a>V této části
 [Ukázková implementace změny hodnot](../../extensibility/debugger/sample-implementation-of-changing-values.md) Pomocí ukázky MyCEE můžete krokovat s procesem změny hodnot.

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)
