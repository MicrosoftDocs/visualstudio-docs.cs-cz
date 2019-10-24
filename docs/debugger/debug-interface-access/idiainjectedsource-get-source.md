---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b389df8220766ffbdbf865a2b8e70877fe91b3f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743340"
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

mimo Vrátí počet bajtů, které představují vrácené bajty. Pokud je `data` `NULL`, pak `pcbData` je celkový počet bajtů dat, která jsou k dispozici.

 `data[]`

mimo Vyrovnávací paměť, která se má vyplnit zdrojovými bajty

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`. Vrátí `S_FALSE`, pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také:
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)