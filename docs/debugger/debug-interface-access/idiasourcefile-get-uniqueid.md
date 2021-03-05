---
description: Načte jednoduchou celočíselnou hodnotu klíče, která je pro tento obrázek jedinečná.
title: 'IDiaSourceFile:: get_uniqueId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0595e20518db1e977a75384c7aec3d1b8cef7716
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147574"
---
# <a name="idiasourcefileget_uniqueid"></a>IDiaSourceFile::get_uniqueId
Načte jednoduchou celočíselnou hodnotu klíče, která je pro tento obrázek jedinečná.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_uniqueId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrací jednoduchou celočíselnou hodnotu klíče, která je pro tento obrázek jedinečná.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Porovnávání klíčů, nikoli řetězců, může urychlit zpracování čísla řádku.

## <a name="see-also"></a>Viz také
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
