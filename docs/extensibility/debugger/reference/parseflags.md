---
description: Určuje, jak se má výraz analyzovat.
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 192e4de399540ce189bbf52cbb0f615b2b9bc855
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222143"
---
# <a name="parseflags"></a>PARSEFLAGS
Určuje, jak se má výraz analyzovat.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Pole
 `PARSE_EXPRESSION`\
 Označuje, že výraz není příkaz.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Označuje, že výraz má být analyzován (a později vyhodnocen) jako adresa.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indikuje, že se výraz analyzuje během doby návrhu (to znamená, když je Návrhář otevřený).

## <a name="remarks"></a>Poznámky
 Předán jako parametr metodám [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) a [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) (Parsování)
