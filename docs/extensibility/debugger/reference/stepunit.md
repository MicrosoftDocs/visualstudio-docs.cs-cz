---
title: STEPUNIT | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a87c86647407d90c9f4292b1307fd5623e85d13b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713512"
---
# <a name="stepunit"></a>STEPUNIT
Určuje krokovou jednotku pro krokování.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>Fields (Pole)
 `STEP_STATEMENT`\
 Kroky podle prohlášení.

 `STEP_LINE`\
 Krok za řádkem.

 `STEP_INSTRUCTION`\
 Kroky podle instrukcí.

## <a name="remarks"></a>Poznámky
 Předánjako argument [step](../../../extensibility/debugger/reference/idebugprocess3-step.md) metody.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)
