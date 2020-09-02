---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac7e825bd33c184d580ada96843366f6d1627f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785189"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje odkaz na vlastnost rámce zásobníku nebo na jinou vlastnost.  
  
> [!NOTE]
> `IDebugReference2` je vyhrazený pro budoucí použití a všechny její metody by měly vracet `E_NOTIMPL` .  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní, aby představovalo odkaz na konkrétní druh hodnoty. Například hodnota může být číselná hodnota jako výsledek vyhodnocení výrazu, kontext paměti použitý pro zobrazení paměti nebo seznam registrů a jejich hodnot.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Pro získání tohoto rozhraní volejte [getReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) . [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) a [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) také vrátí toto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugReference2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Získá strukturu [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , která popisuje tento odkaz.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Nastaví hodnotu tohoto odkazu z řetězce.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Nastaví hodnotu tohoto odkazu z jiného odkazu.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Vytvoří výčet podřízených objektů tohoto odkazu.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Získá nadřazený objekt tohoto odkazu.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Získá nejvíc odvozený odkaz na tento odkaz.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Získá bajty paměti, na které odkazuje tento odkaz.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Získá kontext paměti pro tento odkaz.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Získá velikost tohoto odkazu (v bajtech).|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Nastaví tento typ odkazu.|  
|[Porovnání](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porovná tento odkaz s jiným.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto použití "Property" by nemělo být zaměňováno s tímto významem členské proměnné třídy, i když `IDebugReference2` může představovat takovou entitu.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) představuje vlastnost, zatímco `IDebugReference2` představuje odkaz na vlastnost, obvykle odkaz na objekt v laděném programu.  
  
 Hlavním rozdílem mezi vlastností a odkazem je to, že vlastnost odkazuje na pojmenovanou instanci objektu, zatímco odkaz odkazuje na nepojmenované instance. Vlastnost například může odkazovat na objekt v haldě programu pomocí `"a.b"` . Jiná vlastnost může odkazovat na stejný objekt jako `"c.d"` . Způsob, jakým se odkazuje na tuto vlastnost, vyžaduje, aby `"a.b"` `"c.d"` byl v oboru. Odkaz na stejný objekt je Nameless; na objekt může být odkazováno, dokud je paměť pro tento objekt platná.  
  
 `IDebugProperty2`Rozhraní lze představit jako hodnotu s názvem, typem a adresou. `IDebugReference2`Na druhé straně je možné si představit jako typ a adresu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
