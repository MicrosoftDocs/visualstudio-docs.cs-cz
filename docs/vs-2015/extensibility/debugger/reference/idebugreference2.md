---
title: IDebugReference2 | Dokumentace Microsoftu
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
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1cc7c944fc65adcade14c43a7d158431e9d5578b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736137"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje odkaz na vlastnost rámce zásobníku nebo některé jiné vlastnosti.  
  
> [!NOTE]
>  `IDebugReference2` je vyhrazený pro budoucí použití a všechny jeho metody by měly vrátit `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní představující odkaz na konkrétní typ hodnoty. Hodnota může být například číselnou hodnotu jako výsledek vyhodnocení výrazu, kontext paměti pro zobrazování paměti nebo seznam registrů a jejich hodnoty.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [getreference –](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) k získání tohoto rozhraní. [Getparent –](../../../extensibility/debugger/reference/idebugreference2-getparent.md) a [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) rovněž vracejí toto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugReference2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Získá [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktura, která popisuje tento odkaz.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Nastaví hodnotu tohoto odkazu z řetězce.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Nastaví hodnotu tohoto odkazu z jiného odkazu.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Vytvoří výčet podřízených prvků tohoto odkazu.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Získá nadřazený tento odkaz.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Získá nejvíce odvozenému odkaz na tento odkaz.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Získá počet bajtů paměti, na které odkazuje tento odkaz.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Získá kontext paměti pro tento odkaz.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Získá velikost v bajtech, tento odkaz.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Nastaví tento typ odkazu.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porovná tento odkaz s jiným.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto použití "vlastnosti" neměly by být zaměňovány s znamená členské proměnné třídy, i když `IDebugReference2` může představovat taková entita.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) představuje vlastnost, zatímco `IDebugReference2` představuje odkaz na vlastnost, obvykle odkaz na objekt v programu, který se právě ladí.  
  
 Hlavní rozdíl mezi vlastností a odkaz je, že vlastnost odkazuje na pojmenovanou instanci objektu, zatímco odkaz odkazuje na instanci nepojmenované. Například vlastnost může odkazovat na objekt v haldě tohoto programu pomocí `"a.b"`. Jiné vlastnosti mohou odkazovat na stejný objekt jako `"c.d"`. Změnit způsob odkazující na tuto vlastnost, která vyžaduje `"a.b"` nebo `"c.d"` v oboru. Odkaz na tento stejný objekt je nameless; objekt lze odkazovat jako paměť pro tento objekt je platný.  
  
 `IDebugProperty2` Rozhraní můžete představit jako hodnotu s názvem, typem a adresu. `IDebugReference2`, Na druhé straně, lze považovat za typ a adresu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)

