---
title: CV_access_e | Microsoft Docs
description: Získat informace o typu výčtu CV_access_e, který určuje rozsah viditelnosti (úroveň přístupu) členů v sadě SDK přístup k rozhraní ladění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39b2cfea273d0b98c178c3cf9bcf3894042f760f
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728693"
---
# <a name="cv_access_e"></a>CV_access_e
Určuje rozsah viditelnosti (úroveň přístupu) členských funkcí a proměnných.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementy
Člen CV_private má privátní přístup.

CV_protected člen má chráněný přístup.

CV_public člen má veřejný přístup.

## <a name="remarks"></a>Poznámky
`friend`Specifikátor přístupu zde není obsažen, protože je obvykle používán nečlenské funkce, které mají přístup k soukromým i chráněným prvkům třídy. K vyhledání symbolů s přístupem použijte metodu [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) `SymTagFriend` .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
