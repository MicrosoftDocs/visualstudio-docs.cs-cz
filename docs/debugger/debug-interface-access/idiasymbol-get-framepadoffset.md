---
description: Načte posun z panelu zásobníku z registru ukazatelů na rámec.
title: 'IDiaSymbol:: get_framePadOffset | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadOffset method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 455e617188a58090f3bd6229ab008847912b1f19
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217236"
---
# <a name="idiasymbolget_framepadoffset"></a>IDiaSymbol:: get_framePadOffset

Načte posun z panelu zásobníku z registru ukazatelů na rámec.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_framePadOffset ( 
   DWORD* pPadOffset
);
```

#### <a name="parameters"></a>Parametry

 `pPadOffset`

mimo Vrátí posun panelu zásobníku.

## <a name="return-value"></a>Návratová hodnota

 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky

Tato metoda je podporována počínaje verzí Visual Studio 2019 verze 16,10 Preview 2.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
