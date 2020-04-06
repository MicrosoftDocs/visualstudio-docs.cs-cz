---
title: Kontext vyhodnocení výrazu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738732"
---
# <a name="expression-evaluation-context"></a>Kontext vyhodnocení výrazu
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění kontext **vyhodnocení výrazu**:

- Představuje kontext pro vyhodnocení výrazu. Obecně kontext hodnocení odpovídá lexikální masivu, ve kterém chcete vyhodnotit proměnné, parametry, funkce a metody. Například kontext vyhodnocení výrazu přidružený k rámci zásobníku poskytne kontext pro vyhodnocení místních proměnných, parametrů metody a členů třídy (pokud je k dispozici).

- Existuje, když se program zastavil na zarážky. Samotný výraz je datová struktura představující analyzovaný výraz, který je připraven pro vazbu a vyhodnocení v daném kontextu.

     Podrobněji jsou výrazy vytvářeny pomocí metody [ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Při vyhodnocení výrazu generuje tisknutelný řetězec obsahující název a typ proměnné nebo argumentu a jeho hodnotu. Tento řetězec se zobrazí v okně Kukátko nebo v okně Locals v ide.

     Dané `BSTR` a a [iDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) rozhraní, ladicí modul (DE) můžete vytvořit rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analýzou výrazu. Dané `IDebugExpression2` rozhraní DE můžete získat hodnotu prostřednictvím synchronní nebo asynchronní vyhodnocení výrazu. Tato hodnota spolu s názvem a typem proměnné nebo argumentu je odeslána do ide pro zobrazení.

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazů](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
