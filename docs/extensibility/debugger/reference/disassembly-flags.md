---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fe1515616d6781613961fa11d87005a479c70fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939016"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Určuje příznaky pro zpětný překlad.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Pole
`DF_DOCUMENTCHANGE`\
Označuje, že tato instrukce je v jiném dokumentu než předchozí.

`DF_DISABLED`\
Označuje, že tato instrukce nebude spuštěna.

`DF_INSTRUCTION_ACTIVE`\
Označuje, že tato instrukce je jedním z dalších pokynů, které se mají provést (může jich být více).

`DF_DATA`\
Označuje, že tato instrukce je skutečně data (nikoli kód).

`DF_HASSOURCE`\
Označuje, že tato instrukce má zdroj. Některé pokyny, jako je profilace nebo kód uvolňování paměti, nemají odpovídající zdroj.

`DF_DOCUMENT_CHECKSUM`\
Označuje, že `bstrDocumentUrl` pole obsahuje data kontrolního součtu po adrese URL dokumentu. Informace o tom, jak se ukládají data kontrolního součtu, najdete v části poznámky pro strukturu [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .

## <a name="remarks"></a>Poznámky
Používá se jako `dwFlags` člen struktury [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .

Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
