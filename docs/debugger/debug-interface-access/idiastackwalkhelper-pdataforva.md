---
description: Vrátí blok dat PDATA přidružený k virtuální adrese.
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
ms.openlocfilehash: 91f156d51b787666cf756a4de277587a46b0dd39
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158913"
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
