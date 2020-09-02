---
title: Změna hodnoty místního | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782543"
---
# <a name="changing-the-value-of-a-local"></a>Změna hodnoty místní hodnoty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
   Tento postup se používá také ke změně hodnoty proměnné v okně **kukátka** s tím rozdílem, že se jedná o `IDebugProperty2` objekt přidružený k hodnotě místního, která je použita místo `IDebugProperty2` objektu přidruženého k místnímu objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ukázková implementace změny hodnot](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Pomocí ukázky MyCEE můžete krokovat s procesem změny hodnot.  
  
## <a name="see-also"></a>Viz také  
 [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)
