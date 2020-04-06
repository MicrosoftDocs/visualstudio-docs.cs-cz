---
title: FRAMEINFO_FLAGS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736795"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Určuje informace, které mají být načteny o objektu rámce zásobníku.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Fields (Pole)
`FIF_FUNCNAME`\
Inicializovat/použít `m_bstrFuncName` pole.

`FIF_RETURNTYPE`\
Inicializovat/použít `m_bstrReturnType` pole.

`FIF_ARGS`\
Inicializovat/použít `m_bstrArgs` pole.

`FIF_LANGUAGE`\
Inicializovat/použít `m_bstrLanguage` pole.

`FIF_MODULE`\
Inicializovat/použít `m_bstrModule` pole.

`FIF_STACKRANGE`\
Inicializovat/použít `m_addrMin` `m_addrMax` pole a (rozsah zásobníku).

`FIF_FRAME`\
Inicializovat/použít `m_pFrame` pole.

`FIF_DEBUGINFO`\
Inicializovat/použít `m_fHasDebugInfo` pole.

`FIF_STALECODE`\
Inicializovat/použít `m_fStaleCode` pole.

`FIF_ANNOTATEDFRAME`\
Inicializovat/použít `m_fAnnotatedFrame` pole.

`FIF_DEBUG_MODULEP`\
Inicializovat/použít `m_pModule` pole.

`FIF_FUNCNAME_FORMAT`\
Formátuje název funkce. Výsledek je vrácen `m_bstrFunName` v poli a nejsou vyplněna žádná další pole.

`FIF_FUNCNAME_RETURNTYPE`\
Přidá do pole `m_bstrFuncName` návratový typ.

`FIF_FUNCNAME_ARGS`\
Přidá argumenty do `m_bstrFuncName` pole.

`FIF_FUNCNAME_LANGUAGE`\
Přidá jazyk do `m_bstrFuncName` pole.

`FIF_FUNCNAME_MODULE`\
Přidá název modulu `m_bstrFuncName` do pole.

`FIF_FUNCNAME_LINES`\
Přidá do `m_bstrFuncName` pole počet řádků.

`FIF_FUNCNAME_OFFSET`\
Přidá do `m_bstrFuncName` pole posun v bajtů od začátku řádku, pokud `FIF_FUNCNAME_LINES` je zadán. Pokud `FIF_FUNCNAME_LINES` není zadán, nebo pokud čísla řádků nejsou k dispozici, přidá posun v bajtů od začátku funkce.

`FIF_FUNCNAME_ARGS_TYPES`\
Přidá do pole typ každého `m_bstrFuncName` argumentu funkce.

`FIF_FUNCNAME_ARGS_NAMES`\
Přidá název každého argumentu `m_bstrFuncName` funkce do pole.

`FIF_FUNCNAME_ARGS_VALUES`\
Přidá hodnotu každého argumentu `m_bstrFuncName` funkce do pole.

`FIF_FUNCNAME_ARGS_ALL`\
Přidá do pole typ, název a hodnotu `m_bstrFuncName` všech argumentů.

`FIF_ARGS_TYPES`\
Typy argumentů jsou načteny a formátovány.

`FIF_ARGS_NAMES`\
Názvy argumentů jsou načteny a formátovány.

`FIF_ARGS_VALUES`\
Hodnoty argumentů jsou načteny a formátovány.

`FIF_ARGS_ALL`\
Načtěte a naformátujte typ, název a hodnotu všech argumentů.

`FIF_ARGS_NOFORMAT`\
Určuje, že argumenty nejsou formátovány (například nepřidávejte počáteční a ukončovací závorky kolem seznamu argumentů ani nepřidávejte oddělovač mezi argumenty).

`FIF_ARGS_NO_FUNC_EVAL`\
Určuje, že vyhodnocení funkce (vlastnosti) by nemělo být použito při načítání hodnot argumentů.

`FIF_FILTER_NON_USER_CODE`\
Ladicí modul je filtrovat rámce kódu bez uživatele, takže nejsou zahrnuty.

`FIF_ARGS_NO_TOSTRING`\
Nepovoluj `ToString()` vyhodnocení nebo formátování funkcí při vracení argumentů funkce.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Informace o rámci by měly být získat z hostované domény aplikace spíše než proces hostování.

## <a name="remarks"></a>Poznámky
Tyto příznaky jsou předány [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) a [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metody k označení, která pole mají být inicializována ve struktuře [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) nebo struktury.

Tyto příznaky se také používají k označení, která pole [frameinfo](../../../extensibility/debugger/reference/frameinfo.md) struktury se používají a jsou platné při vrácení struktury. Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
