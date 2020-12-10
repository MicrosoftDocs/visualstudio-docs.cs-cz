---
title: Zápis vyhodnocovacího filtru výrazů společného jazykového modulu runtime | Microsoft Docs
description: Seznamte se s psaním vyhodnocovacího filtru výrazů pro modul CLR (Common Language Runtime), který vyhodnocuje výrazy v laděném jazyce kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1674ae8345873ede5d1b4afb04774d6ed0469b4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996315"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Zápis vyhodnocovacího filtru výrazů společného jazykového modulu runtime
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Vyhodnocení výrazu (EE) je součástí ladicího stroje (DE), který zpracovává syntaxi a sémantiku programovacího jazyka, který vytvořil laděný kód. Výrazy musí být vyhodnoceny v kontextu programovacího jazyka. V některých jazycích například výraz "A + B" znamená "součet a a B". V jiných jazycích může stejný výraz znamenat "A nebo B". Proto musí být pro každý programovací jazyk, který generuje kód objektu pro ladění v integrovaném vývojovém prostředí sady Visual Studio, napsány samostatné EE.

 Některé aspekty ladicího balíčku sady Visual Studio musí interpretovat kód v kontextu programovacího jazyka. Například když se provádění zastaví na zarážce, musí být vyhodnocen a zobrazen libovolný výraz, který uživatel zadal do okna **kukátka** . Uživatel může změnit hodnotu lokální proměnné zadáním výrazu do okna **kukátka** nebo do příkazového **podokna.**

## <a name="in-this-section"></a>V této části
 [CLR (Common Language Runtime) a vyhodnocení výrazu](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Vysvětluje, že při integraci proprietárního programovacího jazyka do integrovaného vývojového prostředí (IDE) sady Visual Studio, psaní EE schopné vyhodnocování výrazů v rámci kontextu vlastního jazyka umožňuje kompilovat do jazyka MSIL (Microsoft Intermediate Language) bez psaní ladicího stroje.

 [Architektura vyhodnocovacího filtru výrazů](../../extensibility/debugger/expression-evaluator-architecture.md) Popisuje implementaci požadovaných rozhraní EE a volání rozhraní API pro Common Language Runtime Provider (SP) a Binder.

 [Registrace vyhodnocovacího filtru výrazů](../../extensibility/debugger/registering-an-expression-evaluator.md) Poznámky, že EE musí registrovat sebe sama jako objekt pro vytváření tříd s modulem CLR (Common Language Runtime) i s běhovými prostředími Visual Studio.

 [Implementace vyhodnocovacího filtru výrazů](../../extensibility/debugger/implementing-an-expression-evaluator.md) Popisuje, jak proces vyhodnocení výrazu obsahuje modul ladění (DE), zprostředkovatele symbolů (SP), objekt pořadače a vyhodnocovací filtr výrazů (EE).

 [Zobrazit místní](../../extensibility/debugger/displaying-locals.md) hodnoty Popisuje, jak, když se provádění pozastaví, ladicí balíček volá DE, aby získal seznam místních proměnných a argumentů.

 [Vyhodnotit výraz okna kukátka](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Dokumentuje, jak balíček ladění sady Visual Studio volá DE k určení aktuální hodnoty každého výrazu v seznamu sledování.

 [Změna hodnoty místní](../../extensibility/debugger/changing-the-value-of-a-local.md) Vysvětluje, že při změně hodnoty místního má každý řádek okna místních hodnot přidružený objekt, který poskytuje název, typ a aktuální hodnotu místní.

 [Implementace typů vizualizace a vlastních prohlížečů](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Vysvětluje, které rozhraní musí implementovat, kterou součást podporuje, aby podporovala typy vizualizací a vlastní prohlížeče.

## <a name="see-also"></a>Viz také
 [Rozšiřitelnost ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
