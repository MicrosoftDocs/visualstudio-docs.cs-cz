---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3f947db7606d6f7495cb1d88591aafa9e9933b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423709"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, jaké informace se mají načíst o objektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Členové  
 FIF_FULLNAME  
 Inicializujte nebo použijte `bstrFullName` pole ve struktuře [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
 FIF_NAME  
 Inicializujte nebo použijte `bstrName` pole ve `FIELD_INFO` struktuře.  
  
 FIF_TYPE  
 Inicializujte nebo použijte `bstrType` pole ve `FIELD_INFO` struktuře.  
  
 FIF_MODIFIERS  
 Inicializujte nebo použijte `bstrModifiers` pole ve `FIELD_INFO` struktuře.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou také předány jako argument metody [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) , aby bylo možné určit, která pole [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury mají být inicializována.  
  
 Tyto hodnoty se používají také v `dwFields` členu `FIELD_INFO` struktury k označení, která pole se používají a jsou platná.  
  
 Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
