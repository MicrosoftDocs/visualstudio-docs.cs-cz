---
title: EVALFLAGS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737119"
---
# <a name="evalflags"></a>EVALFLAGS
Určuje příznaky, které řídí vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EVALFLAGS {
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
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Fields (Pole)
`EVAL_RETURNVALUE`\
Určuje, že vrácená hodnota, pokud existuje, bude vyhodnocena.

`EVAL_NOSIDEEFFECTS`\
Určuje, že vedlejší účinky nebudou povoleny.

`EVAL_ALLOWBPS`\
Určuje zastavení zarážek.

`EVAL_ALLOWERRORREPORT`\
Určuje, že hlášení chyb hostiteli bude povoleno. Používá se především pro vyhodnocení výrazu ve skriptu v aplikaci Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Vynutí vyhodnocení funkcí jako adres, namísto vyvolání funkce.

`EVAL_NOFUNCEVAL`\
Zabrání vyhodnocení funkce. Zvažte například `int` token ve `myExpression(int) + 10`výrazu . Tato funkce může být správně vyhodnocena jako adresa, ale ne jako hodnota.

`EVAL_NOEVENTS`\
Příznak označující, že události, ke kterým dojde během vyhodnocení výrazu by neměly být odeslány do relace ladicí správce (SDM) nebo ide.

## <a name="remarks"></a>Poznámky
Tyto příznaky jsou předány jako argument [metody EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) a [EvaluateSync.](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

Tyto příznaky mohou být kombinovány s bitové OR.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
