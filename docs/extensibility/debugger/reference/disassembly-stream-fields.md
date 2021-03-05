---
description: Určuje informace, které mají být načteny do pole zpětného překladu.
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb45f492a58bd079a1b73212fc9473041d10589
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170468"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Určuje informace, které mají být načteny do pole zpětného překladu.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`DSF_ADDRESS`\
Inicializujte nebo použijte `bstrAddress` pole.

`DSF_ADDRESSOFFSET`\
Inicializujte nebo použijte `bstrAddressOffset` pole.

`DSF_CODEBYTES`\
Inicializujte nebo použijte `bstrCodeBytes` pole.

`DSF_OPCODE`\
Inicializujte nebo použijte `bstrOpCode` pole.

`DSF_OPERANDS`\
Inicializujte nebo použijte `bstrOperands` pole.

`DSF_SYMBOL`\
Inicializujte nebo použijte `bstrSymbol` pole.

`DSF_CODELOCATIONID`\
Inicializujte nebo použijte `uCodeLocationId` pole.

`DSF_POSITION`\
Inicializujte nebo použijte `posBeg` `posEnd` pole a.

`DSF_DOCUMENTURL`\
Inicializujte nebo použijte `bstrDocumentUrl` pole.

`DSF_BYTEOFFSET`\
Inicializujte nebo použijte `dwByteOffset` pole.

`DSF_FLAGS`\
Inicializujte nebo použijte `dwFlags` pole ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Do pole zahrňte názvy symbolů `bstrOperands` .

`DSF_ALL`\
Určuje všechna pole pro datový proud zpětného překladu.

## <a name="remarks"></a>Poznámky
Předán jako parametr metodě [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) k určení, která pole struktury [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) mají být inicializována.

Používá se pro `dwFields` člena `DisassemblyData` struktury k označení, která pole se používají a jsou platná při vrácení struktury.

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Oprávnění](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
