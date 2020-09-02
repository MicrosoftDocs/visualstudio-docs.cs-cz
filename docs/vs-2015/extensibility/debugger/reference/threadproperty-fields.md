---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204810"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, jaké informace o vlákně se mají načíst.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Členové  
 TPF_ID  
 Inicializujte nebo použijte `dwThreadId` pole struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
 TPF_SUSPENDCOUNT  
 Inicializujte nebo použijte `dwSuspendCount` pole `THREADPROPERTIE` struktury S.  
  
 TPF_STATE  
 Inicializujte nebo použijte `dwThreadState` pole `THREADPROPERTIE` struktury S.  
  
 TPF_PRIORITY  
 Inicializujte nebo použijte `bstrPriority` pole `THREADPROPERTIE` struktury S.  
  
 TPF_NAME  
 Inicializujte nebo použijte `bstrName` pole `THREADPROPERTIE` struktury S.  
  
 TPF_LOCATION  
 Inicializujte nebo použijte `bstrLocation` pole `THREADPROPERTIE` struktury S.  
  
 TPF_ALLFIELDS  
 Určuje všechna pole.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou předány jako argument metodě [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) k určení, která pole struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) mají být inicializována.  
  
 Tyto hodnoty se používají také v `dwFields` členu `THREADPROPERTIES` struktury k označení, která pole se používají a jsou platná.  
  
 Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
