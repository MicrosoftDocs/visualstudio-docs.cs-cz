---
title: Implementace vyhodnocovače výrazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c5bf8b782d34cb1375f4357cd33f6e47cc22988
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908454"
---
# <a name="implement-an-expression-evaluator"></a>Implementace vyhodnocovače výrazů
> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka Chyba při vyhodnocování výrazu spravované](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Vyhodnocení výrazu je komplexní souhra grafů mezi ladicího stroje (DE), poskytovatel symbolů (SP), objekt vazače a vyhodnocovací filtr výrazů (EE). Tyto čtyři komponenty jsou připojené rozhraní, které jsou implementované jedna komponenta a využívat jiným.  
  
 EE trvá výrazu z DE ve formě řetězce a analyzuje nebo vyhodnotí ji. EE spustí následující rozhraní, které se spotřebovávají DE:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  EE volá objekt vazače poskytnutých DE, k získání hodnoty symbolů a objekty. EE využívá následujících rozhraní, které jsou implementované DE:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Spouští EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` poskytuje mechanismus pro popisující výsledek vyhodnocení výrazu, jako jsou místní proměnné, jednoduchého typu nebo objekt k sadě Visual Studio, která zobrazí příslušné informace v **lokální**, **Watch** , nebo **okamžité** okna.  
  
  SP je přidělena EE tak DE při požádá o informace. SP spustí rozhraní, které popisují adresy a pole, jako je například následující rozhraní a vy:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE využívá všechny z těchto rozhraní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Strategie implementace vyhodnocovače výrazů](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definuje tří kroků pro výraz strategie implementace vyhodnocovače (EE).  
  
## <a name="see-also"></a>Viz také:  
 [Zápis vyhodnocovací filtr výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)