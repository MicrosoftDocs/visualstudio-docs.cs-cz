---
title: BP_FLAGS90 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738044"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Vyjmenovává platné hodnoty pro volitelné příznaky. Volitelné příznaky lze použít k určení další informace při nastavení zarážky. Tento výčet rozšiřuje [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Fields (Pole)
`BP90_FLAG_NONE`\
Neurčuje žádný příznak zarážky.

`BP90_FLAG_MAP_DOCPOSITION`\
Určuje, že ladicí modul (DE) by měl mapovat zarážku pomocí polohy dokumentu. To platí pouze pro zarážky nastavené ve skriptně orientovaných zdrojových souborech, jako jsou stránky Active Server Pages (ASP).

`BP90_FLAG_DONT_STOP`\
Určuje, že zarážka by měla být zpracována ladicím strojem, ale že ladicí modul by se nakonec neměl zastavit. to znamená, že objekt události [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) by neměl být odeslán. Tento příznak je určen pro použití především s trasovací body.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Používá nativní ladicí modul k určení, zda krokování stavu by měla být vymazána. Liší se od BP90_FLAG_DONT_STOP, protože BP90_FLAG_DONT_STOP není nastavena, pokud trasovací bod spustí makro.

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg90.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
