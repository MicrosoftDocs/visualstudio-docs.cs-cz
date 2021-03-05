---
description: Načte posun na začátek uživatelsky definovaného typu (UDT) člena v UDT.
title: 'IDiaSymbol:: get_offsetInUdt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offsetInUdt method
ms.assetid: 442f20d9-9d6a-44a1-83fb-c3f8c14b6c97
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f02c684ad4a21c64ca45aefa8a9da765e5549fe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155892"
---
# <a name="idiasymbolget_offsetinudt"></a>IDiaSymbol::get_offsetInUdt
Načte posun na začátek uživatelsky definovaného typu (UDT) člena v UDT.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_offsetInUdt( 
   DWORD* pRetVal)
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
 Tato funkce se používá pouze v místních záznamech v optimalizovaném sestavení.

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 KNIHOVNA DLL: msdia100.dll

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
