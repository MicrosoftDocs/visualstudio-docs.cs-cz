---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f44f30b063a34a0d5d5549cd1923b66c1dde9cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864864"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Načte bajty zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

pro Počet bajtů, které představují velikost datové vyrovnávací paměti.

 `pcbData`

mimo Vrátí počet bajtů, které představují vrácené bajty. Pokud `data` je `NULL` , pak `pcbData` je celkový počet bajtů dat, který je k dispozici.

 `data[]`

mimo Vyrovnávací paměť, která se má vyplnit zdrojovými bajty

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)