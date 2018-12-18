---
title: Kontext vyhodnocení | Dokumentace Microsoftu
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
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2643e680afcc29781eca45ab4724c17ae8846285
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772895"
---
# <a name="evaluation-context"></a>Kontext vyhodnocení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka Chyba při vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Když ladicí stroj (DE) volá vyhodnocovací filtr výrazů (EE), tři argumenty předané [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) kontext pro hledání a vyhodnocování symbolů, zjistit, jak je znázorněno v následující tabulce.  
  
## <a name="arguments"></a>Arguments  
  
|Argument|Popis|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) rozhraní, která určuje symbol obslužné rutiny (SH) se použije k určení symbolu.|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) rozhraní, které určuje aktuální bod provádění. To je možné najít metodu, která obsahuje kód, který se spouští.|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) rozhraní, které je možné najít hodnotu a typ symbolu, jeho název.|  
  
 `IDebugParsedExpression::EvaluateSync` Vrátí [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) představující výslednou hodnotu a její typ rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní vyhodnocovače klíčových výrazů](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

