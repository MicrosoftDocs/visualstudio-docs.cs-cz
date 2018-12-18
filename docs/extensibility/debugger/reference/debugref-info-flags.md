---
title: DEBUGREF_INFO_FLAGS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9957b0aaf81048c5040e3f7ff54f3fa9be742dc1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858560"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Určuje, jaké informace se mají načíst informace o ladění referenční objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Členové  
 DEBUGREF_INFO_NAME  
 Inicializace/použít `bstrName` pole ve struktuře.  
  
 DEBUGREF_INFO_TYPE  
 Inicializace/použít `bstrType` pole ve struktuře.  
  
 DEBUGREF_INFO_VALUE  
 Inicializace/použít `bstrValue` pole ve struktuře.  
  
 DEBUGREF_INFO_ATTRIB  
 Inicializace/použít `dwAttrib` pole ve struktuře.  
  
 DEBUGREF_INFO_REFTYPE  
 Inicializace/použít `dwRefType` pole ve struktuře.  
  
 DEBUGREF_INFO_REF  
 Inicializace/použít `pReference` pole ve struktuře.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 V poli hodnota by měla obsahovat hodnotu rozšířit automaticky, pokud je k dispozici pro tento typ objektu.  
  
 DEBUGREF_INFO_NONE  
 Určuje, jestli jsou nastavené žádné příznaky.  
  
 DEBUGREF_INFO_ALL  
 Označuje masku příznaky.  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky jsou předány [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) a [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metody označíte, která pole [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury mají být inicializovány.  
  
 Používá pro `dwFields` člena `DEBUG_REFERENCE_INFO` struktury k označení pole, která se používá a je platný vrátila strukturu.  
  
 Tyto hodnoty lze kombinovat pomocí logické bitové `OR`.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)