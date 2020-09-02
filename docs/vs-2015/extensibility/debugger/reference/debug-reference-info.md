---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 675373ae1728bbca2cc7a89fdaa8014e6286d8b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159329"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Popisuje odkaz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>Členové  
 dwFields  
 Kombinace příznaků z výčtu [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , která určuje, která pole jsou vyplněna.  
  
 BSTR  
 Název objektu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) zadaný uživatelem  
  
 bstrType  
 Odkazový typ jako formátovaný řetězec.  
  
 bstrValue  
 Hodnota reference jako formátovaný řetězec  
  
 dwAttrib  
 Kombinace příznaků z výčtu [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , která určuje příznaky pro atributy vlastností ladění.  
  
 dwRefType  
 Hodnota z výčtu [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) , která určuje, zda je typ odkazu silný nebo slabý.  
  
 m_pReference  
 Objekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , který určuje referenční informace.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je předána voláním metody [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) , která má být vyplněna. Tato struktura je také vrácena jako součást seznamu z rozhraní [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) , který je zase vrácen z volání metody [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
