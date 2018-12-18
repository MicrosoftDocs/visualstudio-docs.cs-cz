---
title: Klíč rozhraní vyhodnocovače výrazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba5affe8bd6b3e787f76863b29233b90a4ec0b72
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230819"
---
# <a name="key-expression-evaluator-interfaces"></a>Rozhraní vyhodnocovače klíčových výrazů
> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka Chyba při vyhodnocování výrazu spravované](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Při zápisu vyhodnocovače výrazů (EE), spolu s kontext vyhodnocení, měli byste se seznámit s následující rozhraní.  
  
## <a name="interface-descriptions"></a>Popis rozhraní  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Obsahuje jedinou metodu, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), která načte do datové struktury, která představuje aktuální bod provádění. Tuto datovou strukturu je jedním ze tří argumentů, které se předá ladicímu stroji (DE) [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) metodu pro vyhodnocení výrazu. Toto rozhraní je obvykle implementována zprostředkovatelem symbol.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Má [svázat](../../extensibility/debugger/reference/idebugbinder-bind.md) metoda, která načte oblast paměti, která obsahuje aktuální hodnotu symbolu. Zadané obě obsahující metodu, reprezentovaný [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objektu a symbolu, reprezentovaný [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objektu, `IDebugBinder::Bind` vrací hodnotu symbolu. `IDebugBinder` Obvykle je implementované moduly DE.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Představuje jednoduchý datový typ. Pro složitější typy, jako jsou pole a metody, použijte odvozené [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) a [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) rozhraní v uvedeném pořadí. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) je jiný důležité odvozené rozhraní, která představuje symboly, který obsahuje jiné symboly, jako jsou metody nebo třídy. `IDebugField` Rozhraní (a odvozené) je většinou implementují moduly poskytovatel symbolů.  
  
     `IDebugField` Objektu lze ji použít k vyhledání názvu a typu symbol nebo společně s [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) objektu, je možné vyhledat její hodnotu.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Představuje bitů za běhu hodnotu symbolu. [Vytvoření vazby](../../extensibility/debugger/reference/idebugbinder-bind.md) přebírá [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objektu, který představuje symbol a vrátí [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objektu. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) vrátí metoda hodnotu symbolu ve vyrovnávací paměti. Zavedenými obvykle implementuje toto rozhraní k reprezentaci hodnoty vlastností v paměti.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Toto rozhraní představuje samotný vyhodnocovací filtr výrazů. Metoda klíče je [analyzovat](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), která vrátí [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) rozhraní.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Toto rozhraní představuje analyzovaný připravený, který se má vyhodnotit výraz. Metoda klíče je [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) která vrátí IDebugProperty2 představující hodnotu a typ výrazu.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Toto rozhraní představuje hodnotu a její typ a je výsledkem vyhodnocení výrazu.  
  
## <a name="see-also"></a>Viz také:  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)