---
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f72a66e6dbfe2749910019760c16f6363498785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804050"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje vlastnost rámce zásobníku, vlastnost dokumentu programu nebo jinou vlastnost. Vlastnost je obvykle výsledkem vyhodnocení výrazu.  
  
> [!NOTE]
> Toto použití "Property" by nemělo být zaměňováno s tímto významem členské proměnné třídy, i když `IDebugProperty2` může představovat takovou entitu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní, aby představovalo konkrétní druh hodnoty. Například hodnota může být číselná hodnota jako výsledek vyhodnocení výrazu, kontext paměti použitý pro zobrazení paměti nebo seznam registrů a jejich hodnot.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Chcete-li získat toto rozhraní, které představuje výsledek vyhodnocení, zavolejte na [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) . `IDebugExpression2::EvaluateAsync` Vrátí toto rozhraní odesláním rozhraní [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) do SDM, které zase volá metodu [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) pro načtení vlastnosti.  
  
 [GetDebugProperty –](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) vrátí toto rozhraní k poskytnutí přidruženého dokumentu skriptu.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) vrátí toto rozhraní, aby reprezentovalo návratovou hodnotu funkce.  
  
 [GetDebugProperty –](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) vrátí toto rozhraní tak, aby reprezentovalo různé vlastnosti programu, jako je název nebo kontext paměti.  
  
 [GetDebugProperty –](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) vrátí toto rozhraní tak, aby reprezentovalo různé vlastnosti rámce zásobníku, jako například místní proměnné.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugProperty2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Vyplní strukturu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , která popisuje vlastnost.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Nastaví hodnotu vlastnosti z řetězce.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Nastaví hodnotu vlastnosti z hodnoty daného odkazu.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Vytvoří výčet podřízených objektů vlastnosti.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Vrátí nadřazený objekt vlastnosti.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Vrátí vlastnost, která popisuje nejvíce odvozenou vlastnost vlastnosti.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Vrátí bajty paměti, které tvoří hodnotu vlastnosti.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Vrátí kontext paměti pro hodnotu vlastnosti.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Vrátí velikost hodnoty vlastnosti v bajtech.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Vrátí odkaz na hodnotu této vlastnosti.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Vrátí rozšířené informace o vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost, reprezentovaná `IDebugProperty2` rozhraním, může být považována za hodnotu s názvem, typem a adresou. Obecně platí, `IDebugProperty2` že může představovat cokoli s hierarchickou strukturou s nadřazenými a podřízenými uzly.  
  
 Vlastnost je obvykle přechodná a trvalá pouze tak dlouho, dokud je aktuální rámec zásobníku, například. Na druhé straně odkaz, který je reprezentován rozhraním [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , trvá, dokud hodnota zůstane v paměti.  
  
 Prostředí IDE může použít `IDebugProperty2` rozhraní, aby uživatelům umožnila Procházet a upravovat vlastnosti za běhu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
