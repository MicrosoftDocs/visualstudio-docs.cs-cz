---
title: MODULE_INFO_FIELDS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714318"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Určuje příznaky pro informace o ladicím modulu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MODULE_INFO_FIELDS { 
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
public enum enum_MODULE_INFO_FIELDS { 
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

## <a name="fields"></a>Fields (Pole)
 `MIF_NONE`\
 Inicializovat/použít žádné pole ve struktuře.

 `MIF_NAME`\
 Inicializovat/použít `m_bstrName` pole ve [struktuře MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Inicializovat/použít `m_bstrUrl` pole `MODULE_INFO` ve struktuře.

 `MIF_VERSION`\
 Inicializovat/použít `m_bstrVersion` pole `MODULE_INFO` ve struktuře.

 `MIF_DEBUGMESSAGE`\
 Inicializovat/použít `m_bstrDebugMessage` pole `MODULE_INFO` ve struktuře.

 `MIF_LOADADDRESS`\
 Inicializovat/použít `m_addrLoadAddress` pole `MODULE_INFO` ve struktuře.

 `MIF_PREFFEREDADDRESS`\
 Inicializovat/použít `m_addrPreferredLoadAddress` pole `MODULE_INFO` ve struktuře.

 `MIF_SIZE`\
 Inicializovat/použít `m_dwSize` pole `MODULE_INFO` ve struktuře.

 `MIF_LOADORDER`\
 Inicializovat/použít `m_dwLoadOrder` pole `MODULE_INFO` ve struktuře.

 `MIF_TIMESTAMP`\
 Inicializovat/použít `m_TimeStamp` pole `MODULE_INFO` ve struktuře.

 `MIF_URLSYMBOLLOCATION`\
 Inicializovat/použít `m_bstrUrlSymbolLocation` pole `MODULE_INFO` ve struktuře.

 `MIF_FLAGS`\
 Inicializovat/použít `m_dwModuleFlags` pole `MODULE_INFO` ve struktuře.

 `MIF_ALLFIELDS`\
 Inicializovat/použít všechna pole `MODULE_INFO` ve struktuře.

## <a name="remarks"></a>Poznámky
 Tyto hodnoty jsou předány jako argument [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metoda k označení, která pole [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury mají být inicializovány.

 Tyto hodnoty se také `MODULE_INFO` používají ve struktuře k označení, která pole se používají a jsou platná.

 Tyto příznaky mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
