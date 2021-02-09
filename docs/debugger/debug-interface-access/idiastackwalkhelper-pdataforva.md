---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d150e777f657fcf63dc66dbe3e686c1b445dd473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863807"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Vrátí blok dat PDATA přidružený k virtuální adrese.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parametry
 `va`

pro Určuje virtuální adresu dat, která se mají získat.

 `cbData`

pro Velikost dat v bajtech, která se má získat

 `pcbData`

mimo Vrátí skutečnou velikost dat v bajtech, které byly získány.

 `pbData`

[in, out] Vyrovnávací paměť, která je vyplněna požadovanými daty. Nemůže být `NULL` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud pro zadanou adresu není k dispozici žádný PDATA. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 PDATA (oddíl s názvem ". pdata") kompilantu obsahuje informace o zpracování výjimek pro funkce.

 Volající ví, kolik dat se má vrátit, aby volající nemusel klást informace o tom, kolik dat je k dispozici. Proto je přijatelné k tomu, aby implementace této metody vrátila chybu, pokud `pbData` je parametr `NULL` .

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)