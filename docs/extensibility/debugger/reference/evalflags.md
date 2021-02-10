---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 073dac8de37edddc1b748c52258047cd2d85e218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937072"
---
# <a name="evalflags"></a>EVALFLAGS
Určuje příznaky, které řídí vyhodnocení výrazu.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Pole
`EVAL_RETURNVALUE`\
Určuje, že návratová hodnota, pokud je vyhodnocena.

`EVAL_NOSIDEEFFECTS`\
Určuje, že vedlejší účinky nejsou povoleny.

`EVAL_ALLOWBPS`\
Určuje zastavení u zarážek.

`EVAL_ALLOWERRORREPORT`\
Určuje zasílání zpráv o chybách do hostitele, který má být povolen. Primárně se používá pro vyhodnocení výrazu ve skriptu v aplikaci Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Vynutí vyhodnocení funkcí jako adres namísto vyvolání funkce.

`EVAL_NOFUNCEVAL`\
Zabraňuje vyhodnocování funkce. Zvažte například `int` token ve výrazu `myExpression(int) + 10` . Tato funkce se může správně vyhodnotit jako adresa, ale ne jako hodnota.

`EVAL_NOEVENTS`\
Příznak označující, že události, ke kterým dojde během vyhodnocení výrazu, by neměly být odesílány do Správce ladění relace (SDM) nebo do rozhraní IDE.

## <a name="remarks"></a>Poznámky
Tyto příznaky jsou předány jako argument metodám [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) a [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .

Tyto příznaky mohou být kombinovány s bitovým nebo.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
