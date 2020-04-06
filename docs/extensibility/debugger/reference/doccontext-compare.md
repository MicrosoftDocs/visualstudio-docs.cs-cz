---
title: DOCCONTEXT_COMPARE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737226"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Určuje kritéria pro porovnání dvou kontextů dokumentu.

## <a name="syntax"></a>Syntaxe

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

## <a name="fields"></a>Fields (Pole)
`DOCCONTEXT_EQUAL`\
Najděte první kontext dokumentu v seznamu, který se rovná kontextu cílového dokumentu.

`DOCCONTEXT_LESS_THAN`\
Najděte první kontext dokumentu v seznamu, který je menší než kontext cílového dokumentu.

`DOCCONTEXT_GREATER_THAN`\
Najděte první kontext dokumentu v seznamu, který je větší než kontext cílového dokumentu.

`DOCCONTEXT_SAME_DOCUMENT`\
Najděte první kontext dokumentu v seznamu, který je ve stejném dokumentu jako kontext cílového dokumentu.

## <a name="remarks"></a>Poznámky
Předánjako argument [compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) metody.

Tyto hodnoty se používají k určení kritérií porovnání pro nalezení prvního kontextu dokumentu v seznamu. Kontext dokumentu je uveden seznam kontextů dokumentu porovnat `IDebugDocumentContext2::Compare` sám proti prostřednictvím metody. První kontext dokumentu v seznamu, pro `true` který je potom vrácenoperátor porovnání.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porovnání](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
