---
title: DEBUG_PROPERTY_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4c4200cb5a44e185d50158829fe44152707ee459
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143036"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obsahuje informace o vlastnosti ladění.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>Členové  
 dwValidFields  
 Kombinace příznaků z výčtu [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , který určuje, která pole jsou vyplněna.  
  
 bstrFullName  
 Úplný název vlastnosti.  
  
 BSTR  
 Název vlastnosti v rámci kontextu.  
  
 bstrType  
 Typ vlastnosti jako formátovaný řetězec.  
  
 bstrValue  
 Hodnota vlastnosti jako formátovaný řetězec.  
  
 pProperty  
 Objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) popsaný touto strukturou.  
  
 dwAttrib  
 Kombinace příznaků z výčtu [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) popisující atributy této vlastnosti.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost je objekt hierarchické povahy, který má název, typ a hodnotu. Vlastnost může například popsat lokální proměnné, parametry, sledovat proměnné a výrazy a Registry.  
  
 Tato struktura je předána metodě [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , kde je vyplněna. Tato struktura je také vrácena jako součást seznamu této struktury z rozhraní [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , které je zase vráceno voláním metod [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) a [enumproperties –](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo –](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
