---
title: CONTEXT_COMPARE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737605"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Určuje kritéria pro porovnání dvou kontextů paměti.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Fields (Pole)
`CONTEXT_EQUAL`\
Najděte první kontext paměti v seznamu, který se rovná kontextu cílové paměti.

`CONTEXT_LESS_THAN`\
Najděte první kontext paměti v seznamu, který je menší než kontext cílové paměti.

`CONTEXT_GREATER_THAN`\
Najděte první kontext paměti v seznamu, který je větší než kontext cílové paměti.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Najděte první kontext paměti v seznamu, který je menší nebo roven kontextu cílové paměti.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Najděte první kontext paměti v seznamu, který je větší nebo roven kontextu cílové paměti.

`CONTEXT_SAME_SCOPE`\
Najděte první kontext paměti v seznamu, který je ve stejném oboru jako kontext cílové paměti.

`CONTEXT_SAME_FUNCTION`\
Najděte první kontext paměti v seznamu, který je ve stejné funkci jako cílový rozsah paměti.

`CONTEXT_SAME_MODULE`\
Najděte první kontext paměti v seznamu, který je ve stejném modulu jako kontext cílové paměti.

`CONTEXT_SAME_PROCESS`\
Najděte první kontext paměti v seznamu, který je ve stejném procesu jako kontext cílové paměti.

## <a name="remarks"></a>Poznámky
Předánjako argument [compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metody.

Tyto hodnoty se používají k nalezení prvního kontextu paměti v seznamu, který splňuje zadaná kritéria porovnání. Kontext paměti je uveden seznam kontextů paměti porovnat `IDebugMemoryContext2::Compare` sám proti prostřednictvím metody. První kontext paměti v seznamu, pro `true` který je potom vrácena operátor porovnání.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porovnání](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
