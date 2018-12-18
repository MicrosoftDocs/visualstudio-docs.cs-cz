---
title: Zobrazení místních hodnot | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e41e77c819a08e1f0440652e023bc2776ba62934
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721886"
---
# <a name="displaying-locals"></a>Zobrazení místních hodnot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka Chyba při vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Spuštění vždycky probíhá v rámci metody, označované také jako obsahující metodu nebo aktuální metoda. Při pozastavení provádění volání sady Visual Studio ladicího stroje (DE) zobrazíte seznam místní proměnné a argumenty, se nazývají lokální proměnné metodu. Visual Studio zobrazí tyto místní hodnoty a jejich hodnoty v **lokální** okna.  
  
 Chcete-li zobrazit místní hodnoty, DE volá [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodu, která náleží EE a dá jí kontext vyhodnocení, který je, poskytovatel symbolů (SP), aktuální adresu spuštění a objekt vazače. Další informace najdete v tématu [kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md). Pokud bude volání úspěšné, `IDebugExpressionEvaluator::GetMethodProperty` vrátí metoda [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objektu, který představuje metodu, která obsahuje aktuální adresu spuštění.  
  
 Volání DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) zobrazíte [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objektu, který je filtrovaná, aby vrátit pouze místní hodnoty a přezkoumána za účelem vytvoření seznamu [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)struktury. Každá struktura obsahuje název, typ a hodnotu lokální. Typ a hodnota jsou uloženy jako formátovaných řetězců vhodnou k zobrazení. Název, typ a hodnota se obvykle zobrazují společně v jednom řádku **lokální** okna.  
  
> [!NOTE]
>  **QuickWatch** a **Watch** proměnné ve stejném formátu název, hodnotu a typ zobrazení systému windows. Ale tyto hodnoty jsou získány pomocí volání [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) místo `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ukázková implementace místních hodnot](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Používají příklady pro jednotlivé kroky v procesu implementace místních hodnot.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)  
 Tento článek vysvětluje, že když se ladicí stroj (DE) volá vyhodnocovací filtr výrazů (EE), předá tři argumenty.  
  
## <a name="see-also"></a>Viz také  
 [Zápis pro vyhodnocovač výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

