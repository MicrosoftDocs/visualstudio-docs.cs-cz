---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: afab1aef58616bfa925fd9f37aacf195eb569c96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462139"
---
# <a name="cv_call_e"></a>CV_call_e
Určuje konvenci volání funkce.

> [!NOTE]
> Zde jsou popsány pouze nejběžnější hodnoty výčtu. Úplný výčet je k dispozici v souboru hlaviček cvconst. h.

## <a name="syntax"></a>Syntax

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
CV_CALL_NEAR_C určuje konvenci volání funkce pomocí téměř zprava doleva. Volající funkce vymaže zásobník.

CV_CALL_NEAR_FAST určuje konvenci volání funkce pomocí blízké nabídky vlevo zleva doprava s Registry. Volaná funkce používá součet bajtů parametrů pro vymazání zásobníku.

CV_CALL_NEAR_STD určuje konvenci volání funkce s použitím volání blížící se standardním volání (nabízená zprava doleva).

CV_CALL_NEAR_SYS určuje konvenci volání funkce pomocí volání téměř systému.

CV_CALL_THISCALL určuje konvenci volání funkce pomocí `this` volání ( `this` ukazatel předaný v registru).

CV_CALL_CLRCALL určuje konvenci volání funkce, kterou používá modul CLR (Common Language Runtime) (označuje se také jako konvence volání spravovaného kódu).

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
