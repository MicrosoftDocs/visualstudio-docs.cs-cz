---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 21c39c553a153707bad707d50cf5a13ae87973fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147754"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní vyčísluje [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní jako součást podpory odkazů na objekty v paměti. Toto rozhraní je nutné implementovat pouze v případě, že jsou podporovány odkazy.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Visual Studio volá [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) k získání tohoto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IEnumDebugReferenceInfo2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Další](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Načte zadaný počet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur v sekvenci výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Přeskočí zadaný počet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur v sekvenci výčtu.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Obnoví posloupnost výčtu na začátek.|  
|[Klonování](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Získá počet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur v enumerátoru.|  
  
## <a name="remarks"></a>Poznámky  
 Odkaz je v podstatě typ a adresa, zatímco vlastnost je název, typ a adresa. Odkaz přetrvává, dokud objekt, na který odkazuje, v paměti. Další podrobnosti najdete v tématu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
