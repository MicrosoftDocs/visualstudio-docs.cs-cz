---
title: BP_FLAGS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738059"
---
# <a name="bp_flags"></a>BP_FLAGS
Obsahuje volitelné příznaky, které mohou být použity k určení další informace při nastavování zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Fields (Pole)
`BP_FLAG_NONE`\
Neurčuje žádný příznak zarážky.

`BP_FLAG_MAP_DOCPOSITION`\
Určuje, že ladicí modul (DE) by měl mapovat zarážku pomocí polohy dokumentu. To platí pouze pro zarážky nastavené ve skriptně orientovaných zdrojových souborech, jako jsou stránky Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Určuje, že zarážka by měla být zpracována ladicím strojem, ale že ladicí modul by se nakonec neměl zastavit (to znamená, že objekt události [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) by neměl být odeslán). Tento příznak je určen pro použití především s trasovací body.

## <a name="remarks"></a>Poznámky
Používá se `dwFlags` pro členy [struktury BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
