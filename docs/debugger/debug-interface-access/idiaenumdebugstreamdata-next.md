---
title: 'IDiaEnumDebugStreamData:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eb951dd2362b93c61e835da78e5e02d6dc67069
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857039"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Načte zadaný počet záznamů ve výčtové sekvenci.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet záznamů, které mají být načteny.

 cbData

pro Velikost vyrovnávací paměti dat (v bajtech).

 pcbData

mimo Vrátí počet vrácených bajtů. Pokud `data` má hodnotu null, pak `pcbData` obsahuje celkový počet bajtů dat dostupných pro všechny požadované záznamy.

 data []

mimo Vyrovnávací paměť, která se má vyplnit daty záznamu streamu ladění.

 pceltFetched

[in, out] Vrátí počet záznamů v `data` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda nejsou k dispozici žádné další záznamy. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)