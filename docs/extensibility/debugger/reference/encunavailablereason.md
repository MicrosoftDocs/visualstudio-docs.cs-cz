---
title: EncUnavailableReason | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737166"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Představuje důvody, které **upravit a pokračovat** není k dispozici.

## <a name="syntax"></a>Syntaxe

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Fields (Pole)
`ENCUN_NONE`\
Není k dispozici žádný konkrétní důvod, proč není k dispozici možnost Upravit a pokračovat.

`ENCUN_INTEROP`\
Upravit a pokračovat není k dispozici během interop volání.

`ENCUN_SQLCLR`\
Upravit a pokračovat není k dispozici během volání procedury SQL, který používá modul CLR (Common Language Runtime).

`ENCUN_MINIDUMP`\
Upravit a pokračovat není k dispozici při zpracování mini-dump.

`ENCUN_EMBEDDED`\
Upravit a pokračovat není k dispozici při zpracování vloženého kódu.

`ENCUN_ATTACH`\
Upravit a pokračovat není k dispozici, protože relace byla připojena k ladicímu programu, nikoli spuštěna.

`ENCUN_WIN64`\
Úpravy a pokračování nejsou při zpracování 64bitového kódu systému Windows k dispozici.

## <a name="remarks"></a>Poznámky
Tento výčet je určen pouze [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]pro interní použití společností . [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) a [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) metody implementované dodavatelem vlastního `E_NOTIMPL`portu by měl y vždy vrátit .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.idl

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
