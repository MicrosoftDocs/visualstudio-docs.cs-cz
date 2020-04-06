---
title: EVALFLAGS90 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737099"
---
# <a name="evalflags90"></a>EVALFLAGS90
Vyjmenová vhodnotit platné hodnoty pro příznaky, které řídí vyhodnocení výrazu. Tento výčet rozšiřuje výčtu [EVALFLAGS.](../../../extensibility/debugger/reference/evalflags.md)

## <a name="syntax"></a>Syntaxe

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

## <a name="fields"></a>Fields (Pole)
`EVAL90_RETURNVALUE`\
Určuje, že vrácená hodnota, pokud existuje, bude vyhodnocena.

`EVAL90_NOSIDEEFFECTS`\
Určuje, že vedlejší účinky nebudou povoleny.

`EVAL90_ALLOWBPS`\
Určuje zastavení zarážek.

`EVAL90_ALLOWERRORREPORT`\
Určuje, že má být povoleno hlášení chyb hostiteli. Používá se především pro vyhodnocení výrazu ve skriptu v aplikaci Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Vynutí vyhodnocení funkcí jako adres, namísto vyvolání funkce.

`EVAL90_NOFUNCEVAL`\
Zabrání vyhodnocení funkce. Zvažte například `int` token ve `myExpression(int) + 10`výrazu . Tato funkce může být správně vyhodnocena jako adresa, ale ne jako hodnota.

`EVAL90_NOEVENTS`\
Příznak označující, že události, ke kterým dojde během vyhodnocení výrazu by neměly být odeslány do relace ladicí správce (SDM) nebo ide.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Umožňuje vyhodnocení výrazu v době návrhu.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Umožňuje implicitní vytvoření proměnné.

`EVAL90_FORCE_EVALUATION_NOW`\
Vynutí okamžité vyhodnocení. To je užitečné při obsluhě požadavku, jako je například požadavek uživatele.

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg90.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
