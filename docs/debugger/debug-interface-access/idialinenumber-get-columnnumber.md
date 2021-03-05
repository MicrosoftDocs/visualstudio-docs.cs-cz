---
description: Načte číslo sloupce, kde začíná výraz nebo příkaz.
title: 'IDiaLineNumber:: get_columnNumber | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 06d2dc2f703f74d5a3964ee3eb1a1fff948a50ad
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148302"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
Načte číslo sloupce, kde začíná výraz nebo příkaz.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí číslo sloupce, kde začíná výraz nebo příkaz. Pokud je hodnota nulová, informace o sloupci nejsou k dispozici.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnota sloupce vrácená touto metodou je posun bajtů na řádek na první znak příkazu na řádku.

## <a name="see-also"></a>Viz také
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
