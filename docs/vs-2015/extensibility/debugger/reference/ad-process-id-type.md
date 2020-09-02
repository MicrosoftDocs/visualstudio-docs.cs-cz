---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d471a73205383f0f23c5016872712a3ba2c578d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153614"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, jak interpretovat ID procesu ve struktuře [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Členové  
 AD_PROCESS_ID_SYSTEM  
 ID procesu je systémový identifikátor. Použijte `ProcessId.dwProcessId` pole struktury [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
 AD_PROCESS_ID_GUID  
 ID procesu je identifikátor GUID. Použijte `ProcessId.guidProcessId` pole `AD_PROCESS_ID` struktury.  
  
## <a name="remarks"></a>Poznámky  
 Používá se pro `ProcessIdType` členy [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury k identifikaci typu ID procesu, který je obsažen ve struktuře. Určuje, jak se má `ProcessId` ve struktuře interpretovat sjednocení.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
