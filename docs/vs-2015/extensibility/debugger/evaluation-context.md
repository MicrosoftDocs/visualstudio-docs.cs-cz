---
title: Kontext vyhodnocení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7dae6ddcb0c75f0dcbc2207465aed522a4210159
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831752"
---
# <a name="evaluation-context"></a>Kontext vyhodnocení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Když ladicí stroj (DE) volá vyhodnocovací filtr výrazů (EE), tři argumenty předané do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) určují kontext pro hledání a vyhodnocení symbolů, jak je znázorněno v následující tabulce.  
  
## <a name="arguments"></a>Arguments  
  
|Argument|Popis|  
|--------------|-----------------|  
|`pSymbolProvider`|Rozhraní [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) , které určuje obslužnou rutinu symbolu (SH), která se má použít k identifikaci symbolu.|  
|`pAddress`|Rozhraní [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , které určuje aktuální bod provádění. To lze použít k vyhledání metody, která obsahuje prováděný kód.|  
|`pBinder`|Rozhraní [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) , které lze použít k vyhledání hodnoty a typu symbolu daného názvu.|  
  
 `IDebugParsedExpression::EvaluateSync` Vrátí rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) představující výslednou hodnotu a její typ.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní vyhodnocovacích výrazů výrazu Key](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
