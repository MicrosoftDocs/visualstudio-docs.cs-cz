---
title: FIELD_KIND_EX | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0c13d83f80b311838eca32945462c1f17ca23f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736874"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Vyjmenovává další druhy polí, které může objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obsahovat. Tento výčet rozšiřuje [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>Fields (Pole)
`FIELD_KIND_EX_NONE`\
Pole neobsahuje rozšířený typ.

`FIELD_TYPE_EX_METHODVAR`\
Pole obsahuje proměnnou metody.

`FIELD_TYPE_EX_CLASSVAR`\
Pole obsahuje proměnnou třídy.

## <a name="requirements"></a>Požadavky
Záhlaví: Sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
