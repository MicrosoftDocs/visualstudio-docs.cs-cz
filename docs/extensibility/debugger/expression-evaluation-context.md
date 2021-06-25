---
title: Kontextová | Microsoft Docs
description: Přečtěte si o kontextu vyhodnocení výrazu, který představuje kontext pro vyhodnocení výrazu a existuje, když se program zastaví na zarážce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73eeafb95c7e4d52f69109c5eb7c06eb48bd8d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901211"
---
# <a name="expression-evaluation-context"></a>Kontext vyhodnocení výrazu
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění kontext vyhodnocení **výrazu**:

- Představuje kontext pro vyhodnocení výrazu. Obecně platí, že kontext vyhodnocení odpovídá lexikální oboru, ve kterém se mají vyhodnotit proměnné, parametry, funkce a metody. Například kontext vyhodnocení výrazu přidružený k rámu zásobníku poskytne kontext pro vyhodnocení místních proměnných, parametrů metody a členů třídy (pokud jsou k dispozici).

- Existuje, když se program zastaví na zarážce. Samotný výraz je datová struktura představující parsovaný výraz, který je připravený k vytvoření vazby a vyhodnocení v daném kontextu.

     Výrazy se podrobněji vytvářejí pomocí metody [ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Při vyhodnocení výrazu vygeneruje tisknutelný řetězec obsahující název a typ proměnné nebo argumentu a jeho hodnotu. Tento řetězec se zobrazí v okně okno Kukátko nebo v okně Místní hodnoty integrovaného vývojového prostředí.)

     Vzhledem k `BSTR` rozhraní [a IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) může ladicí modul (DE) vytvořit rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) parsací výrazu. Vzhledem k `IDebugExpression2` rozhraní může DE získat hodnotu prostřednictvím synchronního nebo asynchronního vyhodnocení výrazu. Tato hodnota spolu s názvem a typem proměnné nebo argumentu se odesílá do integrovaného vývojového prostředí (IDE) k zobrazení.

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazů](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
