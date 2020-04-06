---
title: EXCEPTION_STATE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736953"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Určuje stav výjimky.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Fields (Pole)
`EXCEPTION_NONE`\
Nezastavujte se u výjimky.

`EXCEPTION_STOP_FIRST_CHANCE`\
Zastavte při prvním spuštění výjimky. Při popisu události výjimky tento příznak označuje, že událost výjimky je událost výjimky první šance.

`EXCEPTION_STOP_SECOND_CHANCE`\
Zastavte na druhé vypalování výjimky. Při popisu události výjimky označuje, že událost výjimky je událost výjimky druhé šance.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Zastavit při prvním spuštění výjimky uživatelského režimu. Při popisu události výjimky označuje, že událost výjimky je událost výjimky uživatele první šance.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Zastavte, pokud není zachycena výjimka uživatelského režimu. Při popisu události výjimky označuje, že událost výjimky je událost výjimky nezachyceného uživatelského režimu.

`EXCEPTION_STOP_ALL`\
Zastavit na jakékoli výjimky. Nepoužívá se při popisu události výjimky.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Při popisu události výjimky označuje, že výjimku nelze dále z.

`EXCEPTION_CODE_SUPPORTED`\
Označuje, že výjimka má kód, který ji podporuje. Používá se při zobrazení výjimky

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Označuje, že kód výjimky by měl být zobrazen v šestnáctkové. Používá se při zobrazení výjimky.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Označuje, že kód výjimky podporuje JustMyCode. Používá se při zobrazení výjimky.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Označuje, že ladicí program spravovaného kódu by měl zpracovávat výjimky. Pokud není nastavena, výchozí ladicí program zpracovává výjimky. To je [předána SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metody a není použit ve [struktuře EXCEPTION_INFO.](../../../extensibility/debugger/reference/exception-info.md)

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

## <a name="remarks"></a>Poznámky
Používá se `dwState` jako člen [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury k označení stavu výjimky a co lze s ní udělat.

Tyto hodnoty jsou také [předány SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metoda nastavit stav všech výjimek.

Tyto příznaky mohou být kombinovány s bitové OR.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
