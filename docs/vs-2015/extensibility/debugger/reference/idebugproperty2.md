---
title: IDebugProperty2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc5e780bb5e211b8900a22b181749e0376c6f242
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742624"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje vlastnost rámce zásobníku, vlastnost dokumentu program nebo některé jiné vlastnosti. Vlastnost je obvykle výsledkem vyhodnocení výrazu.  
  
> [!NOTE]
>  Toto použití "vlastnosti" neměly by být zaměňovány s znamená členské proměnné třídy, i když `IDebugProperty2` může představovat taková entita.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní představující konkrétní typ hodnoty. Hodnota může být například číselnou hodnotu jako výsledek vyhodnocení výrazu, kontext paměti pro zobrazování paměti nebo seznam registrů a jejich hodnoty.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) získat toto rozhraní, která reprezentuje výsledek hodnocení. `IDebugExpression2::EvaluateAsync` Vrátí toto rozhraní odesláním [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) rozhraní SDM, která pak volá [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) načíst vlastnost.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) vrátí toto rozhraní k poskytování přidruženého skriptovacího dokumentu.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) vrátí toto rozhraní k reprezentaci návratovou hodnotu funkce.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) vrátí toto rozhraní k reprezentaci různé vlastnosti programu, jako je například název, nebo místní paměti.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) vrátí toto rozhraní k reprezentaci různých vlastností rámce zásobníku, jako jsou místní proměnné.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugProperty2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Vyplní [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktura, která popisuje vlastnosti.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Nastaví hodnotu vlastnosti z řetězce.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Nastaví hodnotu vlastnosti z hodnoty daného odkazu.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Vytvoří výčet podřízené vlastnosti.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Vrací nadřazeného člena vlastnost.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Vrátí vlastnosti, která popisuje vlastnosti nejvíce odvozenému vlastnosti.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Vrátí počet bajtů paměti, které tvoří hodnotu vlastnosti.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Vrátí kontext paměti pro hodnotu vlastnosti.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Vrátí velikost v bajtech, hodnota vlastnosti.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Vrátí odkaz na hodnotu této vlastnosti.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Vrátí rozšířené informace o vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost, reprezentovaný hodnotou `IDebugProperty2` rozhraní, si lze představit jako hodnotu s názvem, typem a adresu. Další obecné řečeno `IDebugProperty2` může představovat cokoli, co má hierarchickou strukturu s nadřazených a podřízených uzlů.  
  
 Vlastnost je obvykle přechodné, například trvající pouze tak dlouho, dokud aktuální rámec zásobníku. Na druhé straně odkazu, reprezentovaný hodnotou [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) rozhraní, má platnost tak dlouho, dokud hodnota zůstane v paměti.  
  
 Integrované vývojové prostředí můžete použít `IDebugProperty2` rozhraní umožňuje uživatelům procházení a změna vlastností za běhu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

