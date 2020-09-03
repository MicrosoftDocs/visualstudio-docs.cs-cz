---
title: Namesearchoptions – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d721ebc5849fc459d24173ad0500b4b1c12260f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182970"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje možnosti hledání symbolů a názvů souborů.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum NameSearchOptions {   
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
 `nsNone`  
 Nejsou zadány žádné možnosti.  
  
 `nsfCaseSensitive`  
 Použije shodu názvů rozlišující velká a malá písmena.  
  
 `nsfCaseInsensitive`  
 Použije porovnávání názvů bez rozlišení velkých a malých písmen.  
  
 `nsfFNameExt`  
 Považuje názvy za cesty a použije název souboru. přípona rozšíření se shoduje s názvem.  
  
 `nsfRegularExpression`  
 Aplikuje název rozlišovat velikost písmen pomocí hvězdičky (*) a otazníků (?) jako zástupných znaků.  
  
 `nsfUndecoratedName`  
 Platí pouze pro symboly, které mají nedekorované i dekorované názvy.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty z tohoto výčtu jsou předány do následujících metod:  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2. h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession:: findChildren –](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession:: FindFile –](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
