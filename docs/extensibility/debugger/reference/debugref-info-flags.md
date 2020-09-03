---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737385"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Určuje, jaké informace se mají načíst o ladicím objektu reference.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`DEBUGREF_INFO_NAME`\
Inicializujte nebo použijte `bstrName` pole ve struktuře.

`DEBUGREF_INFO_TYPE`\
Inicializujte nebo použijte `bstrType` pole ve struktuře.

`DEBUGREF_INFO_VALUE`\
Inicializujte nebo použijte `bstrValue` pole ve struktuře.

`DEBUGREF_INFO_ATTRIB`\
Inicializujte nebo použijte `dwAttrib` pole ve struktuře.

`DEBUGREF_INFO_REFTYPE`\
Inicializujte nebo použijte `dwRefType` pole ve struktuře.

`DEBUGREF_INFO_REF`\
Inicializujte nebo použijte `pReference` pole ve struktuře.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Pole hodnota by mělo obsahovat automaticky rozbalenou hodnotu, je-li k dispozici, pro tento typ objektu.

`DEBUGREF_INFO_NONE`\
Označuje, že nejsou nastavené žádné příznaky.

`DEBUGREF_INFO_ALL`\
Označuje masku příznaků.

## <a name="remarks"></a>Poznámky
Tyto příznaky jsou předány metodám [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) a [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) , které označují, která pole [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury mají být inicializována.

Používá se pro `dwFields` člena `DEBUG_REFERENCE_INFO` struktury k označení, která pole se používají a jsou platná při vrácení struktury.

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
