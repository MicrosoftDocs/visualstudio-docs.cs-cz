---
description: Určuje stav výjimky.
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 297c5de3afd2b5f81444dd29278fc294cd71aa6a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059441"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Určuje stav výjimky.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`EXCEPTION_NONE`\
Nestavte u výjimky.

`EXCEPTION_STOP_FIRST_CHANCE`\
Zastavit při prvním vyvolávání výjimky. Při popisu události výjimky označuje tento příznak, že událost výjimky je první pravděpodobnost události.

`EXCEPTION_STOP_SECOND_CHANCE`\
Zastavení při druhém vyvolávání výjimky. Při popisu události výjimky označuje, že událost výjimky je událost výjimky s druhou pravděpodobností.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Zastavte se při prvním vyvolávání výjimky v uživatelském režimu. Při popisu události výjimky označuje, že událost výjimky je první událost výjimky uživatele.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Zastavit, pokud není zachycena výjimka uživatelského režimu. Při popisu události výjimky označuje, že událost výjimky je nezachycená událost výjimky v uživatelském režimu.

`EXCEPTION_STOP_ALL`\
Zastavte jakoukoli výjimku. Nepoužívá se při popisu události výjimky.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Při popisu události výjimky označuje, že výjimka nemůže pokračovat z.

`EXCEPTION_CODE_SUPPORTED`\
Označuje, že výjimka má kód, který ho podporuje. Používá se při zobrazení výjimky.

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Označuje, že kód výjimky by měl být zobrazen v šestnáctkovém formátu. Používá se při zobrazení výjimky.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Označuje, že kód výjimky podporuje JustMyCode. Používá se při zobrazení výjimky.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Označuje, že má ladicí program spravovaného kódu zpracovávat výjimky. Pokud není nastaveno, výchozí ladicí program zpracuje výjimky. Tato metoda je předána metodě [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) a nepoužívá se ve struktuře [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) .

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
ZASTARALÉ, NEPOUŽÍVEJTE.

## <a name="remarks"></a>Poznámky
Slouží jako `dwState` člen struktury [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) k označení stavu výjimky a o tom, co se na něj dá dělat.

Tyto hodnoty jsou také předány metodě [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) pro nastavení stavu všech výjimek.

Tyto příznaky mohou být kombinovány s bitovým nebo.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
