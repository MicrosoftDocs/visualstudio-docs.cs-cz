---
title: Zobrazení místních obyvatel | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738928"
---
# <a name="display-locals"></a>Zobrazit místní obyvatele
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Provádění vždy probíhá v rámci metody, označované také jako obsahující metoda nebo aktuální metoda. Při pozastavení provádění Visual Studio volá ladicí modul (DE) získat seznam místních proměnných a argumentů, souhrnně nazývá místní metody. Visual Studio zobrazí tyto místní a jejich hodnoty v okně **Locals.**

 Chcete-li zobrazit místní, DE volá [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metoda patřící do EE a dává mu kontext hodnocení, to znamená, že zprostředkovatel symbol (SP), aktuální adresu spuštění a objekt pořadače. Další informace naleznete v [tématu Hodnocení kontextu](../../extensibility/debugger/evaluation-context.md). Pokud je volání úspěšné, `IDebugExpressionEvaluator::GetMethodProperty` metoda vrátí objekt [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) který představuje metodu, která obsahuje aktuální adresu spuštění.

 DE volá [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) získat [Objekt IEnumDebugPropertyInfo2,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) který je filtrován vrátit pouze locals a výčtu k vytvoření seznamu [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktur. Každá struktura obsahuje název, typ a hodnotu místní. Typ a hodnota jsou uloženy jako formátované řetězce, vhodné pro zobrazení. Název, typ a hodnota jsou obvykle zobrazeny společně v jednom řádku okna **Locals.**

> [!NOTE]
> Okna **QuickWatch** a **Watch** také zobrazují proměnné se stejným formátem názvu, hodnoty a typu. Tyto hodnoty jsou však získány voláním [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) namísto `IDebugProperty2::EnumChildren`.

## <a name="in-this-section"></a>V tomto oddílu
 [Ukázková implementace místních obyvatel](../../extensibility/debugger/sample-implementation-of-locals.md) Používá příklady krokovat proces implementace místních obyvatel.

## <a name="related-sections"></a>Související oddíly
 [Souvislosti hodnocení](../../extensibility/debugger/evaluation-context.md) Vysvětluje, že když ladicí modul (DE) volá vyhodnocení výrazu (EE), předá tři argumenty.

## <a name="see-also"></a>Viz také
 [Napsat vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
