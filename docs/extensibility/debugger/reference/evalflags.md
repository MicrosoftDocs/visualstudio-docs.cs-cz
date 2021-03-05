---
description: Určuje příznaky, které řídí vyhodnocení výrazu.
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
ms.openlocfilehash: 531d155104475b84d881358711a6aa3f1d0bf2ce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150936"
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
