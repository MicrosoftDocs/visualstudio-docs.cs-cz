---
title: 'IDiaSymbol:: get_isDataAligned | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00507b5d69f46657968407170d9633f1d84c8e4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463426"
---
# <a name="idiasymbolget_isdataaligned"></a>IDiaSymbol::get_isDataAligned
Načte příznak, který určuje, zda byl uživatelem definovaný typ (UDT) zarovnán na určitou konkrétní hranici paměti.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isDataAligned(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí, zda byl typ `TRUE` UDT zarovnán na určitou hranici paměti. v opačném případě vrátí hodnotu `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je obecně nastavena, když je spustitelný soubor kompilován s nevýchozím zarovnáním dat. Například kompilátor jazyka Microsoft C++ může změnit zarovnání dat pomocí možnosti příkazového řádku/zp <em>#</em> , kde *#* je bajtová hodnota.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)