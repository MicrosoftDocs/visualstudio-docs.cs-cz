---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204812"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Popisuje vlastnosti vlákna.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Členové  
 dwFields  
 Kombinace příznaků z výčtu [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , která popisuje, která pole v této struktuře jsou platná.  
  
 dwThreadId  
 ID vlákna.  
  
 dwSuspendCount  
 Počet pozastavení vlákna  
  
 dwThreadState  
 Hodnota z výčtu [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) označující stav operačního vlákna.  
  
 bstrPriority  
 Řetězec určující prioritu vlákna; například "vyšší normální", "normální" nebo "čas kritický".  
  
 bstName  
 Název vlákna.  
  
 bstrLocation  
 Umístění vlákna (obvykle vrchní rámec zásobníku), obvykle vyjádřené jako název metody, kde je provádění aktuálně zastaveno.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je vyplněna voláním metody [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Informace, které jsou tak vráceny, se obvykle používají v naplnění okna **vlákna** .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
