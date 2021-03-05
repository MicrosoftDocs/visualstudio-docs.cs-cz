---
description: Načte posun umístění symbolu.
title: 'IDiaSymbol:: get_offset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8c5c3e59596fdfc1e769710f8459620303e72d6a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155899"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
Načte posun umístění symbolu. Použijte, pokud je [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` nebo `LocIsBitField` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí posun v bajtech umístění symbolu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Posun je z dříve stanoveného známého bodu. Například posun pro `LocIsBitField` typ umístění je obvykle od začátku obsahující třídy.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
