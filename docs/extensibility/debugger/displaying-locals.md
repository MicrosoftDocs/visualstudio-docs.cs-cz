---
title: Zobrazení místních hodnot | Microsoft Docs
description: Seznamte se se seznamem místních proměnných a argumentů, které jsou souhrnně označovány jako lokální hodnoty metody, které jsou zobrazeny při pozastavení provádění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 564b42a15e1420027b79cb5f00c70f61649ad4f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097263"
---
# <a name="display-locals"></a>Zobrazit místní hodnoty
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Spuštění vždy probíhá v kontextu metody, označované také jako obsažená metoda nebo aktuální metoda. Po pozastavení provádění aplikace Visual Studio zavolá ladicí modul (DE), aby získal seznam místních proměnných a argumentů, které jsou souhrnně označovány jako lokální proměnné metody. Visual Studio zobrazí tyto místní a jejich hodnoty v okně **místní** hodnoty.

 Chcete-li zobrazit národní prostředí, metoda DE volá metodu [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) , která patří k EE, a poskytuje IT kontext pro vyhodnocení, to znamená, že poskytovatel symbolů (SP), aktuální adresa spuštění a objekt pořadače. Další informace naleznete v tématu [vyhodnocení kontextu](../../extensibility/debugger/evaluation-context.md). Pokud je volání úspěšné, `IDebugExpressionEvaluator::GetMethodProperty` Metoda vrátí objekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , který představuje metodu, která obsahuje aktuální adresu spuštění.

 Příkaz DE volá [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) k získání objektu [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , který je filtrován tak, aby vracel pouze místní a výčty, aby vytvořil seznam [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury. Každá struktura obsahuje název, typ a hodnotu místní. Typ a hodnota jsou uloženy jako formátované řetězce vhodné pro zobrazení. Název, typ a hodnota se obvykle zobrazují společně na jednom řádku okna **místní** hodnoty.

> [!NOTE]
> Okna **QuickWatch** a **Watch** také zobrazují proměnné se stejným formátem jako název, hodnota a typ. Tyto hodnoty jsou však získány voláním metody [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) namísto `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>V této části
 [Ukázková implementace místních hodnot](../../extensibility/debugger/sample-implementation-of-locals.md) Používá příklady pro krokování procesu implementace lokálních hodnot.

## <a name="related-sections"></a>Související oddíly
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md) Vysvětluje, že když ladicí modul (DE) volá vyhodnocovací filtr výrazů (EE), předává tři argumenty.

## <a name="see-also"></a>Viz také
 [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
