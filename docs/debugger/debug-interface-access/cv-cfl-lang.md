---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745338"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Určuje jazyk zdrojového kódu pro aplikaci nebo propojený modul.

## <a name="syntax"></a>Syntaxe

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Elementy
Jazyk aplikace CV_CFL_C je C.

Jazyk aplikace CV_CFL_CXX je C++.

CV_CFL_FORTRAN aplikační jazyk je FORTRAN.

CV_CFL_MASM aplikační jazyk je Microsoft Macro Assembler.

Jazyk aplikace CV_CFL_PASCAL je Pascal.

Jazyk aplikace CV_CFL_BASIC je základní.

Jazyk aplikace CV_CFL_COBOL je COBOL.

Aplikace CV_CFL_LINK je modulem generovaným linkerem.

CV_CFL_CVTRES aplikace je modul prostředků převedený nástrojem CVTRES.

CV_CFL_CVTPGD aplikace je modul optimalizovaný pro POGO generovaný pomocí nástroje CVTPGD.

Jazyk aplikace CV_CFL_CSHARP je C#.

Jazyk aplikace CV_CFL_VB je Visual Basic.

Jazyk aplikace CV_CFL_ILASM je sestavení zprostředkujícího jazyka (to znamená sestavení CLR).

Jazyk aplikace CV_CFL_JAVA je Java.

Jazyk aplikace CV_CFL_JSCRIPT je JScript.

CV_CFL_MSIL aplikace je neznámý jazyk MSIL (Microsoft Intermediate Language), pravděpodobně výsledkem použití přepínače [/LTCG (generování kódu při propojování)](/cpp/build/reference/ltcg-link-time-code-generation) .

CV_CFL_HLSL jazyk aplikace je jazyk shaderu na vysoké úrovni.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také:
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
