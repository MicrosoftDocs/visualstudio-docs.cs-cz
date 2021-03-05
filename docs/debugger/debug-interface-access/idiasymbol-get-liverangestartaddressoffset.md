---
description: Vrátí odkládací část počáteční adresy rozsahu, ve kterém je místní symbol platný.
title: 'IDiaSymbol:: get_liveRangeStartAddressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 41cdaaa1035a27294f3172c6533da2f682ff69a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156032"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Vrátí odkládací část počáteční adresy rozsahu, ve kterém je místní symbol platný.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Parametry
 `offset`

mimo Vrátí odkládací část počátečního rozsahu adres.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

> [!NOTE]
> Vrácený kód chyby znamená, že symbol neobsahuje informace o živém rozsahu.

## <a name="remarks"></a>Poznámky
 Adresa vytvořená oddílem a odsazením je začátek rozsahu, ve kterém je symbol platný.

 Chcete-li získat část této adresy, použijte [IDiaSymbol:: get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 KNIHOVNA DLL: msdia100.dll

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
