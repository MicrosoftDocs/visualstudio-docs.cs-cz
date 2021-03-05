---
description: Představuje důvody, proč není k dispozici úprava a pokračování.
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1f80dc1454cb1c15feddd099411bcb339dbc58c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151001"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Představuje důvody, proč není k dispozici **Úprava a pokračování** .

## <a name="syntax"></a>Syntax

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Pole
`ENCUN_NONE`\
Žádný konkrétní důvod, proč není dostupná úprava a pokračování.

`ENCUN_INTEROP`\
Funkci upravit a pokračovat nelze použít při volání InterOp.

`ENCUN_SQLCLR`\
Příkaz Upravit a pokračovat není k dispozici během volání procedury SQL, které používá modul CLR (Common Language Runtime).

`ENCUN_MINIDUMP`\
Příkaz Upravit a pokračovat není k dispozici při zpracování zkráceného výpisu.

`ENCUN_EMBEDDED`\
Při zpracování vloženého kódu není tato úprava a pokračování k dispozici.

`ENCUN_ATTACH`\
Příkaz Upravit a pokračovat není k dispozici, protože relace byla připojena ke službě, kterou nespustil nástroj, ladicí program.

`ENCUN_WIN64`\
Příkaz Upravit a pokračovat není při zpracování 64ho kódu systému Windows k dispozici.

## <a name="remarks"></a>Poznámky
Tento výčet je určen pouze pro interní použití [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . Metody [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) a [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) , jak je implementuje vlastní dodavatel portu, by měly vždycky vracet `E_NOTIMPL` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. idl

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
