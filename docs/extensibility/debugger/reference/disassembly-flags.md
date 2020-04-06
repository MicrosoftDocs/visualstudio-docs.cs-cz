---
title: DISASSEMBLY_FLAGS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737369"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Určuje příznaky pro demontáž.

## <a name="syntax"></a>Syntaxe

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

## <a name="fields"></a>Fields (Pole)
`DF_DOCUMENTCHANGE`\
Označuje, že tato instrukce je v jiném dokumentu než předchozí.

`DF_DISABLED`\
Označuje, že tato instrukce nebude provedena.

`DF_INSTRUCTION_ACTIVE`\
Označuje, že tento pokyn je jedním z dalších pokynů, které mají být provedeny (může být více než jeden).

`DF_DATA`\
Označuje, že tato instrukce je opravdu data (ne kód).

`DF_HASSOURCE`\
Označuje, že tato instrukce má zdroj. Některé pokyny, například profilování nebo kód uvolňování paměti, nemají žádný odpovídající zdroj.

`DF_DOCUMENT_CHECKSUM`\
Označuje, `bstrDocumentUrl` že pole obsahuje data kontrolního součtu za adresou URL dokumentu. Informace o způsobu ukládání dat kontrolního součtu naleznete v části Poznámky pro strukturu [DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

## <a name="remarks"></a>Poznámky
Používá se `dwFlags` jako člen struktury [DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

Tyto příznaky mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
