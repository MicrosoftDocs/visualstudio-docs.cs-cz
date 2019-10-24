---
title: 'IDiaStackWalkHelper:: readMemory – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741365"
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

mimo Vrátí počet bajtů, které jsou ve skutečnosti čteny. Pokud je `pbData` `NULL`, pak toto je celkový počet bajtů, které jsou k dispozici.

 `pbData`

[in, out] Vyrovnávací paměť, která je vyplněna čtenou pamětí.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také:
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum – výčet](../../debugger/debug-interface-access/memorytypeenum.md)