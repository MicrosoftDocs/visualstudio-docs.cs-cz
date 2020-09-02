---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c66894fe0515b28037bbb2a19715fa09cbf9fa62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153593"
---
# <a name="attach_reason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje důvod pro modul ladění (DE), který se má připojit k uzlu programu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Členové  
 ATTACH_REASON_AUTO  
 Připojte se, protože proces je aktuálně v režimu ladění.  
  
 ATTACH_REASON_LAUNCH  
 Připojte se, protože proces byl spuštěn.  
  
 ATTACH_REASON_USER  
 Připojte se kvůli žádosti uživatele.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty se používají jako parametr pro metody [připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md) a [připojení](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Pojovat](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Připojit](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
