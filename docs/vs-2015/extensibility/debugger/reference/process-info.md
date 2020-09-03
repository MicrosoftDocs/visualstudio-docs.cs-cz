---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205021"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obsahuje informace o procesu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Členové  
 Pole  
 Kombinace příznaků z výčtu [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) , které určují, která pole jsou vyplněna.  
  
 bstrFileName  
 Úplný název cesty procesu. Ekvivalent volání metody [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) s parametrem `GN_FILENAME` .  
  
 bstrBaseName  
 Název souboru a přípona procesu. Ekvivalent volání `IDebugProcess2::Getname` metody s parametrem `GN_BASENAME` .  
  
 bstrTitle  
 Název procesu, pokud existuje. Ekvivalent volání `IDebugProcess2::Getname` metody s parametrem `GN_TITLE` .  
  
 ID  
 Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , která identifikuje proces. Ekvivalent volání metody [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
 dwSessionId  
 Identifikátor relace ladění, ve které tento proces běží.  
  
 bstrAttachedSessionName  
 Název připojené relace. Ekvivalent volání metody [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
 CreationTime  
 Čas vytvoření procesu.  
  
 Příznaky  
 Kombinace příznaků z výčtu [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) , které určují vlastnosti procesu.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je předána metodě [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) , kde je vyplněna.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
