---
description: Vytvoří výčet platných hodnot příznaků, které řídí vyhodnocení výrazu.
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e75b938f45df5d4fa91bec4b59964dfc6a54e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095924"
---
# <a name="evalflags90"></a>EVALFLAGS90
Vytvoří výčet platných hodnot příznaků, které řídí vyhodnocení výrazu. Tento výčet rozšiřuje výčet [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) .

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Pole
`EVAL90_RETURNVALUE`\
Určuje, že návratová hodnota, pokud je vyhodnocena.

`EVAL90_NOSIDEEFFECTS`\
Určuje, že vedlejší účinky nejsou povoleny.

`EVAL90_ALLOWBPS`\
Určuje zastavení u zarážek.

`EVAL90_ALLOWERRORREPORT`\
Určuje, že zasílání zpráv o chybách do hostitele má být povoleno. Primárně se používá pro vyhodnocení výrazu ve skriptu v aplikaci Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Vynutí vyhodnocení funkcí jako adres namísto vyvolání funkce.

`EVAL90_NOFUNCEVAL`\
Zabraňuje vyhodnocování funkce. Zvažte například `int` token ve výrazu `myExpression(int) + 10` . Tato funkce se může správně vyhodnotit jako adresa, ale ne jako hodnota.

`EVAL90_NOEVENTS`\
Příznak označující, že události, ke kterým dojde během vyhodnocení výrazu, by neměly být odesílány do Správce ladění relace (SDM) nebo do rozhraní IDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Povolí vyhodnocení výrazu v době návrhu.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Povoluje vytváření implicitních proměnných.

`EVAL90_FORCE_EVALUATION_NOW`\
Vynutí, aby vyhodnocování probíhalo okamžitě. To je užitečné při obsluhování žádosti, jako je například požadavek uživatele.

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg90. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
