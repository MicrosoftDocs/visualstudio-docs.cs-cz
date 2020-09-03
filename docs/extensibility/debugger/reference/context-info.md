---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737568"
---
# <a name="context_info"></a>CONTEXT_INFO
Tato struktura popisuje kontext paměti nebo kontext kódu.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Členové
`dwFields`\
Kombinace příznaků od [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) výčtu, která určuje, která pole jsou vyplněna<strong>.</strong>

`bstrModuleUrl`\
Název modulu, ve kterém je umístěn kontext.

`bstrFunction`\
Název funkce, kde se nachází kontext.

`posFunctionOffset`\
Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , která identifikuje posunutí řádku a sloupce funkce přidružené k kontextu kódu.

`bstrAddress`\
Adresa v kódu, kde je umístěn daný kontext.

`bstrAddressOffset`\
Posun adresy v kódu, kde je umístěn daný kontext.

`bstrAddressAbsolute`\
Absolutní adresa v paměti, kde je umístěn daný kontext.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena ze volání metody [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) .

Typické použití této struktury je v podpoře okna ladění **paměti** .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
