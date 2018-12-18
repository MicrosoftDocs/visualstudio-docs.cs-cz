---
title: IDebugReference2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5d5d8b3ab6e608a2454847fc9ec27e384777bc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121496"
---
# <a name="idebugreference2"></a>IDebugReference2
Toto rozhraní představuje odkaz na vlastnost rámce zásobníku nebo některé jiné vlastnosti.  
  
> [!NOTE]
>  `IDebugReference2` je vyhrazeno pro budoucí použití a všechny její metody by měla vrátit `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní představující odkaz na konkrétní typ hodnoty. Hodnota může být například číselnou hodnotu výsledkem vyhodnocení výrazu, kontextu paměť použitá pro zobrazení paměti nebo seznam registry a jejich hodnoty.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [getreference –](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) k získání tohoto rozhraní. [Getparent –](../../../extensibility/debugger/reference/idebugreference2-getparent.md) a [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) toto rozhraní se taky vrátit.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugReference2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Získá [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktura, která popisuje tento odkaz.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Nastaví hodnotu tohoto odkazu z řetězce.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Nastaví hodnotu tohoto odkazu z jiného odkazu.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Vytvoří výčet podřízené objekty tohoto odkazu.|  
|[Getparent –](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Získá nadřazený tohoto odkazu.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Získá odkaz na většinou odvozených tohoto odkazu.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Získá počet bajtů paměti, na které odkazuje tento odkaz.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Získá kontext paměti u tohoto odkazu.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Získá velikost v bajtech tohoto odkazu.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Nastaví tento typ odkazu.|  
|[Porovnání](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porovná tento odkaz s jinou.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto použití "vlastnosti" by neměl Nezaměňovat s znamená členské proměnné třídy, i když `IDebugReference2` může představovat taková entita.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) představuje vlastnost, zatímco `IDebugReference2` představuje odkaz na vlastnost, obvykle odkaz na objekt v programu laděné.  
  
 Hlavní rozdíl mezi vlastností a odkaz je, že vlastnost odkazuje na pojmenovanou instanci objektu, zatímco odkaz odkazuje na nepojmenované instance. Například vlastnost mohou odkazovat na objekt v programu haldy podle `"a.b"`. Jinou vlastnost mohou odkazovat na stejný objekt jako `"c.d"`. Způsob odkazující na tuto vlastnost vyžaduje, aby `"a.b"` nebo `"c.d"` být v oboru. Odkaz na tento stejný objekt je nameless; objekt lze odkazovat tak dlouho, dokud paměť pro tento objekt je platný.  
  
 `IDebugProperty2` Rozhraní si lze představit jako hodnotu s název, typ a adresu. `IDebugReference2`, Na dalším ruční, lze považovat za typ a adresu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [Getreference –](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)