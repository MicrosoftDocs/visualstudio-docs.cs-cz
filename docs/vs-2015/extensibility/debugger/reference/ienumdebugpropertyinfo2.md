---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee305083957f6d2f2ada09aec1747497fcf6db68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147831"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní vyčísluje [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní, aby reprezentovalo informace pro konkrétní vlastnost.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Zavolejte [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pro získání tohoto rozhraní, které představuje podřízené objekty určité vlastnosti. Zavolejte [enumproperties –](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) pro získání tohoto rozhraní, které představuje vlastnosti konkrétního bloku zásobníku.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IEnumDebugPropertyInfo2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Další](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Načte zadaný počet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur v sekvenci výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Přeskočí zadaný počet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur v sekvenci výčtu.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Obnoví posloupnost výčtu na začátek.|  
|[Klonování](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Získá počet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur v enumerátoru.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí, že vlastnost je hierarchií informací, které mohou obsahovat název, hodnotu, adresu a typ, jakož i všechny další informace, které jsou vhodné pro přidružený objekt vlastnosti nebo rámec zásobníku. Další podrobnosti najdete v tématu [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
