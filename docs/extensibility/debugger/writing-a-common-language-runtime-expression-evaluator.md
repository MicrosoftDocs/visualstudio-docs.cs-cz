---
title: Psaní revaluorátoru exprese běžného běhu za běhu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712326"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Psaní relgenivátoru exprese za běhu běžného jazyka
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Vyhodnocení výrazu (EE) je část ladicího modulu (DE), který zpracovává syntaxi a sémantiku programovacího jazyka, který produkoval kód, který je laděn. Výrazy musí být vyhodnoceny v kontextu programovacího jazyka. Například v některých jazycích výraz "A+B" znamená "součet A a B.". V jiných jazycích může stejný výraz znamenat "A nebo B". Proto musí být napsáno samostatné EE pro každý programovací jazyk, který generuje objektový kód, který má být laděn v ide sady Visual Studio.

 Některé aspekty balíčku ladění sady Visual Studio musí interpretovat kód v kontextu programovacího jazyka. Například při spuštění zastaví na zarážku, všechny výrazy, které uživatel zadal do okna **sledování** musí být vyhodnoceny a zobrazeny. Uživatel může změnit hodnotu místní proměnné zadáním výrazu do okna **Kukátka** nebo do okna **Okamžité.**

## <a name="in-this-section"></a>V tomto oddílu
 [Společné jazykové runtime a vyhodnocení výrazu](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Vysvětluje, že při integraci proprietární programovací jazyk do ide Sady Visual Studio, psaní EE schopné vyhodnocení výrazy v kontextu proprietární ho jazyka umožňuje kompilovat do zprostředkující jazyk Microsoft (MSIL) bez psaní ladicí modul.

 [Architektura vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator-architecture.md) Popisuje, jak implementovat požadovaná rozhraní EE a volat zprostředkovatele symbolů modulu RUNTIME (SP) a rozhraní pořadače jazyka.

 [Registrace vyhodnocení výrazu](../../extensibility/debugger/registering-an-expression-evaluator.md) Konstatuje, že EE musí zaregistrovat sám jako továrna třídy s běžným jazykem runtime a Visual Studio runtime prostředí.

 [Implementace vyhodnocení výrazu](../../extensibility/debugger/implementing-an-expression-evaluator.md) Popisuje, jak proces vyhodnocení výrazu zahrnuje ladicí modul (DE), zprostředkovatel symbolu (SP), objekt pořadače a vyhodnocení výrazu (EE).

 [Zobrazit místní obyvatele](../../extensibility/debugger/displaying-locals.md) Popisuje, jak při pozastavení spuštění ladicí balíček volá DE získat seznam místních proměnných a argumentů.

 [Vyhodnocení výrazu okna kukátka](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Dokumentuje, jak balíček ladění sady Visual Studio volá DE k určení aktuální hodnoty každého výrazu v seznamu sledovaných položek.

 [Změna hodnoty místního](../../extensibility/debugger/changing-the-value-of-a-local.md) Vysvětluje, že při změně hodnoty local, každý řádek locals okna má přidružený objekt, který poskytuje název, typ a aktuální hodnotu místní.

 [Implementace vizualizérů typů a vlastních prohlížečů](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Vysvětluje, které rozhraní musí být implementováno, kterou komponentou pro podporu vizualizátorů typů a vlastních prohlížečů.

## <a name="see-also"></a>Viz také
 [Rozšiřitelnost ladicího programu visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
