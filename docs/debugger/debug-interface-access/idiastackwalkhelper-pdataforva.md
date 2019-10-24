---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741404"
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

[in, out] Vyrovnávací paměť, která je vyplněna požadovanými daty. Nelze `NULL`.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`. Vrátí `S_FALSE`, pokud pro zadanou adresu není k dispozici žádný PDATA. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 PDATA (oddíl s názvem ". pdata") kompilantu obsahuje informace o zpracování výjimek pro funkce.

 Volající ví, kolik dat se má vrátit, aby volající nemusel klást informace o tom, kolik dat je k dispozici. Proto je přijatelné k tomu, aby implementace této metody vrátila chybu, pokud je parametr `pbData` `NULL`.

## <a name="see-also"></a>Viz také:
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)