---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f273bbab4a85f03a7da0d155d8b9e081693987c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912967"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Určuje kritéria pro porovnání dvou kontextů paměti.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`CONTEXT_EQUAL`\
Najde první kontext paměti v seznamu, který je stejný jako cílový kontext paměti.

`CONTEXT_LESS_THAN`\
Najde první kontext paměti v seznamu, který je menší než cílový kontext paměti.

`CONTEXT_GREATER_THAN`\
Najde první kontext paměti v seznamu, který je větší než cílový kontext paměti.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Najde první kontext paměti v seznamu, který je menší nebo roven cílovému kontextu paměti.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Najde první kontext paměti v seznamu, který je větší nebo roven cílovému kontextu paměti.

`CONTEXT_SAME_SCOPE`\
Najde první kontext paměti v seznamu, který je ve stejném oboru jako cílový kontext paměti.

`CONTEXT_SAME_FUNCTION`\
Najde první kontext paměti v seznamu, který je ve stejné funkci jako cílový rozsah paměti.

`CONTEXT_SAME_MODULE`\
Najde první kontext paměti v seznamu, který je ve stejném modulu jako cílový kontext paměti.

`CONTEXT_SAME_PROCESS`\
Najde první kontext paměti v seznamu, který je ve stejném procesu jako cílový kontext paměti.

## <a name="remarks"></a>Poznámky
Byl předán jako argument metody [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .

Tyto hodnoty se používají k vyhledání prvního paměťového kontextu v seznamu, který splňuje zadaná kritéria porovnání. Kontextu paměti je předána seznam kontextů paměti pro porovnání sebe sama s `IDebugMemoryContext2::Compare` metodou. První kontext paměti v seznamu, pro který je vrácen operátor porovnání `true` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porovnání](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
