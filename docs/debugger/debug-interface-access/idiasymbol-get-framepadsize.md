---
description: Načte dodatečnou velikost panelu přidanou do každé funkce.
title: 'IDiaSymbol:: get_framePadSize | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d361ec3e144730e49345d3560f815ee5fe0be469
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217224"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol:: get_framePadSize

Načte dodatečnou velikost panelu přidanou do každé funkce.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>Parametry

 `pPadSize`

mimo Vrátí další velikost panelu přidanou do každé funkce.

## <a name="return-value"></a>Návratová hodnota

 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky

Velikost nadbytečného panelu se obvykle používá v části Upravit a pokračovat.

Tato metoda je podporována počínaje verzí Visual Studio 2019 verze 16,10 Preview 2.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
