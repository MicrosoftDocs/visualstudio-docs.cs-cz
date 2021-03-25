---
description: Vytvoří výčet dalších druhů polí, které může objekt IDebugField obsahovat.
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75c1839987901edc9bc3571fa303ca0d3218a53c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059389"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Vytvoří výčet dalších druhů polí, které může objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obsahovat. Tento výčet rozšiřuje výčet [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) .

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`FIELD_KIND_EX_NONE`\
Pole neobsahuje rozšířený typ.

`FIELD_TYPE_EX_METHODVAR`\
Pole obsahuje proměnnou metody.

`FIELD_TYPE_EX_CLASSVAR`\
Pole obsahuje proměnnou třídy.

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
