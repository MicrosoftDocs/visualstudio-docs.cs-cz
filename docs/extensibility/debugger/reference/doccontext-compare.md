---
description: Určuje kritéria pro porovnávání dvou kontextů dokumentu.
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6eeee3e31c898660930b676df716fe25769bbb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096002"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Určuje kritéria pro porovnávání dvou kontextů dokumentu.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Pole
`DOCCONTEXT_EQUAL`\
Najde první kontext dokumentu v seznamu, který se rovná kontextu cílového dokumentu.

`DOCCONTEXT_LESS_THAN`\
Najde první kontext dokumentu v seznamu, který je menší než kontext cílového dokumentu.

`DOCCONTEXT_GREATER_THAN`\
Najde první kontext dokumentu v seznamu, který je větší než kontext cílového dokumentu.

`DOCCONTEXT_SAME_DOCUMENT`\
Najde první kontext dokumentu v seznamu, který je ve stejném dokumentu jako kontext cílového dokumentu.

## <a name="remarks"></a>Poznámky
Byl předán jako argument metody [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .

Tyto hodnoty se používají k určení kritérií porovnání pro hledání prvního kontextu dokumentu v seznamu. Kontextu dokumentu je uveden seznam kontextů dokumentů pro porovnání sebe sama s `IDebugDocumentContext2::Compare` metodou. První kontext dokumentu v seznamu, pro který je vrácen operátor porovnání `true` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porovnání](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
