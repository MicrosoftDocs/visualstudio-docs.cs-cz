---
description: Přečte blok dat z image spustitelného souboru v paměti.
title: 'IDiaStackWalkHelper:: readMemory – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a70cc9660e872a3e64e202d7498814b3aa24daa3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158885"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Přečte blok dat z image spustitelného souboru v paměti.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Parametry
 `type`

pro Hodnota z výčtu [výčtu memorytypeenum –](../../debugger/debug-interface-access/memorytypeenum.md) určující typ paměti, která se má číst.

 VA

pro Virtuální adresa v imagi, ze které se má začít číst.

 `cbData`

pro Velikost vyrovnávací paměti dat v bajtech

 `pcbData`

mimo Vrátí počet bajtů, které jsou ve skutečnosti čteny. Pokud `pbData` je `NULL` , pak toto je celkový počet bajtů dat, která jsou k dispozici.

 `pbData`

[in, out] Vyrovnávací paměť, která je vyplněna čtenou pamětí.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum – výčet](../../debugger/debug-interface-access/memorytypeenum.md)
