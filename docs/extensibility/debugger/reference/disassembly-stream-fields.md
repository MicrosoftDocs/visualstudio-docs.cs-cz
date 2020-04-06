---
title: DISASSEMBLY_STREAM_FIELDS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737365"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Určuje, jaké informace se má načíst o poli demontáže.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Fields (Pole)
`DSF_ADDRESS`\
Inicializovat/použít `bstrAddress` pole.

`DSF_ADDRESSOFFSET`\
Inicializovat/použít `bstrAddressOffset` pole.

`DSF_CODEBYTES`\
Inicializovat/použít `bstrCodeBytes` pole.

`DSF_OPCODE`\
Inicializovat/použít `bstrOpCode` pole.

`DSF_OPERANDS`\
Inicializovat/použít `bstrOperands` pole.

`DSF_SYMBOL`\
Inicializovat/použít `bstrSymbol` pole.

`DSF_CODELOCATIONID`\
Inicializovat/použít `uCodeLocationId` pole.

`DSF_POSITION`\
Inicializovat/použít `posBeg` `posEnd` pole a.

`DSF_DOCUMENTURL`\
Inicializovat/použít `bstrDocumentUrl` pole.

`DSF_BYTEOFFSET`\
Inicializovat/použít `dwByteOffset` pole.

`DSF_FLAGS`\
Inicializovat/použít `dwFlags` pole ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Do pole zahrňte názvy symbolů. `bstrOperands`

`DSF_ALL`\
Určuje všechna pole pro demontáž datového proudu.

## <a name="remarks"></a>Poznámky
Předánjako parametr [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metoda k označení, která pole [disassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury mají být inicializovány.

Používá se `dwFields` pro `DisassemblyData` člen struktury k označení, která pole se používají a jsou platné při vrácení struktury.

Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
