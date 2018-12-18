---
title: MODULE_INFO_FIELDS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf01cb2573922adb5d8b5b4bc26b10b839009dda
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832847"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Určuje příznaky pro ladicí informace modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Členové  
 MIF_NONE  
 Inicializace/použití žádné z polí ve struktuře.  
  
 MIF_NAME  
 Inicializace/použít `m_bstrName` pole [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury.  
  
 MIF_URL  
 Inicializace/použít `m_bstrUrl` pole `MODULE_INFO` struktury.  
  
 MIF_VERSION  
 Inicializace/použít `m_bstrVersion` pole `MODULE_INFO` struktury.  
  
 MIF_DEBUGMESSAGE  
 Inicializace/použít `m_bstrDebugMessage` pole `MODULE_INFO` struktury.  
  
 MIF_LOADADDRESS  
 Inicializace/použít `m_addrLoadAddress` pole `MODULE_INFO` struktury.  
  
 MIF_PREFFEREDADDRESS  
 Inicializace/použít `m_addrPreferredLoadAddress` pole `MODULE_INFO` struktury.  
  
 MIF_SIZE  
 Inicializace/použít `m_dwSize` pole `MODULE_INFO` struktury.  
  
 MIF_LOADORDER  
 Inicializace/použít `m_dwLoadOrder` pole `MODULE_INFO` struktury.  
  
 MIF_TIMESTAMP  
 Inicializace/použít `m_TimeStamp` pole `MODULE_INFO` struktury.  
  
 MIF_URLSYMBOLLOCATION  
 Inicializace/použít `m_bstrUrlSymbolLocation` pole `MODULE_INFO` struktury.  
  
 MIF_FLAGS  
 Inicializace/použít `m_dwModuleFlags` pole `MODULE_INFO` struktury.  
  
 MIF_ALLFIELDS  
 Inicializace/použít všechna pole v `MODULE_INFO` struktury.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou předány jako argument [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) indikace které pole [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury mají být inicializovány.  
  
 Tyto hodnoty jsou také používány v `MODULE_INFO` struktury k označení pole, která se používá a je platný.  
  
 Tyto příznaky lze kombinovat pomocí logické bitové `OR`.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)