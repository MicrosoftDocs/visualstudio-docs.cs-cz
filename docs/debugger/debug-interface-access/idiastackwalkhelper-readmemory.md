---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc768db3f42f610a8efd30cea567e721929cb291
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464693"
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