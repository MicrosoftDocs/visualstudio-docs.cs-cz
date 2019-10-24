---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745357"
---
# <a name="cv_call_e"></a>CV_call_e
Určuje konvenci volání funkce.

> [!NOTE]
> Zde jsou popsány pouze nejběžnější hodnoty výčtu. Úplný výčet je k dispozici v souboru hlaviček cvconst. h.

## <a name="syntax"></a>Syntaxe

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Elementy
CV_CALL_NEAR_C určuje konvenci volání funkce s použitím téměř zprava doleva. Volající funkce vymaže zásobník.

CV_CALL_NEAR_FAST určuje konvenci volání funkce pomocí blízké nabídky vlevo zleva doprava s Registry. Volaná funkce používá součet bajtů parametrů pro vymazání zásobníku.

CV_CALL_NEAR_STD určuje konvenci volání funkce s použitím volání blížící se ke standardnímu volání (nabízená zprava doleva).

CV_CALL_NEAR_SYS určuje konvenci volání funkce za použití volání téměř systému.

CV_CALL_THISCALL určuje konvenci volání funkce pomocí volání `this` (ukazatel `this` předaný v registru).

CV_CALL_CLRCALL určuje konvenci volání funkce, kterou používá modul CLR (Common Language Runtime) (označuje se také jako konvence volání spravovaného kódu).

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také:
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
