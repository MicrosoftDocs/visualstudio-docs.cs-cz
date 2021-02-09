---
title: Namesearchoptions – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c63d38e1b4d79227cfdc694dc6d8c154a01532f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853210"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Určuje možnosti hledání symbolů a názvů souborů.

## <a name="syntax"></a>Syntax

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Elementy
`nsNone` Nejsou zadány žádné možnosti.

`nsfCaseSensitive` Použije shodu názvů rozlišující velká a malá písmena.

`nsfCaseInsensitive` Použije porovnávání názvů bez rozlišení velkých a malých písmen.

`nsfFNameExt` Považuje názvy za cesty a použije název souboru. přípona rozšíření se shoduje s názvem.

`nsfRegularExpression` Aplikuje název rozlišovat velikost písmen pomocí hvězdičky (*) a otazníků (?) jako zástupných znaků. (Jiné běžné znaky regulárních výrazů se nepodporují.)

`nsfUndecoratedName` Platí pouze pro symboly, které mají nedekorované i dekorované názvy.

## <a name="remarks"></a>Poznámky
Hodnoty z tohoto výčtu jsou předány do následujících metod:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
