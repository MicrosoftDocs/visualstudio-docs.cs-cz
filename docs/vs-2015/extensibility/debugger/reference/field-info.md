---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e18e906cbc65ea811e765553a8d2711b3e4eb0f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423735"
---
# <a name="field_info"></a>FIELD_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato struktura popisuje místní proměnnou, parametr nebo jiné pole.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Členové  
 dwFields  
 Kombinace příznaků z výčtu [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) , které určují členy, kteří jsou vyplněni.  
  
 bstrFullName  
 Celé jméno pole  
  
 BSTR  
 Krátký název pole.  
  
 bstrType  
 Typ pole.  
  
 dwModifiers  
 Kombinace příznaků z výčtu [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) , který popisuje pole.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je předána metodě [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) , kde je vyplněna.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
