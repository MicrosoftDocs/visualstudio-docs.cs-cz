---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 116eb36cf96284698a6d93730db39bb38d22b93e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938704"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Určuje příznaky pro informace o ladicím modulu.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
 `MIF_NONE`\
 Inicializujte nebo použijte žádné z polí ve struktuře.

 `MIF_NAME`\
 Inicializujte nebo použijte `m_bstrName` pole ve struktuře [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 `MIF_URL`\
 Inicializujte nebo použijte `m_bstrUrl` pole ve `MODULE_INFO` struktuře.

 `MIF_VERSION`\
 Inicializujte nebo použijte `m_bstrVersion` pole ve `MODULE_INFO` struktuře.

 `MIF_DEBUGMESSAGE`\
 Inicializujte nebo použijte `m_bstrDebugMessage` pole ve `MODULE_INFO` struktuře.

 `MIF_LOADADDRESS`\
 Inicializujte nebo použijte `m_addrLoadAddress` pole ve `MODULE_INFO` struktuře.

 `MIF_PREFFEREDADDRESS`\
 Inicializujte nebo použijte `m_addrPreferredLoadAddress` pole ve `MODULE_INFO` struktuře.

 `MIF_SIZE`\
 Inicializujte nebo použijte `m_dwSize` pole ve `MODULE_INFO` struktuře.

 `MIF_LOADORDER`\
 Inicializujte nebo použijte `m_dwLoadOrder` pole ve `MODULE_INFO` struktuře.

 `MIF_TIMESTAMP`\
 Inicializujte nebo použijte `m_TimeStamp` pole ve `MODULE_INFO` struktuře.

 `MIF_URLSYMBOLLOCATION`\
 Inicializujte nebo použijte `m_bstrUrlSymbolLocation` pole ve `MODULE_INFO` struktuře.

 `MIF_FLAGS`\
 Inicializujte nebo použijte `m_dwModuleFlags` pole ve `MODULE_INFO` struktuře.

 `MIF_ALLFIELDS`\
 Inicializujte nebo použijte všechna pole ve `MODULE_INFO` struktuře.

## <a name="remarks"></a>Poznámky
 Tyto hodnoty jsou předány jako argument metody [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) , aby označovaly, která pole [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury mají být inicializována.

 Tyto hodnoty se používají také ve `MODULE_INFO` struktuře k označení, která pole se používají a jsou platná.

 Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
