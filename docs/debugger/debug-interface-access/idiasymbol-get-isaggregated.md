---
title: 'IDiaSymbol:: get_isAggregated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02e1a3a831ccd7394c58af4b744f0be8b905d763
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463482"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Načte příznak, který určuje, zda je datový symbol součástí agregace nebo kolekce symbolů; Kompilátor bude považovat agregované symboly za samostatné entity, ale ve skutečnosti jsou součástí jednoho většího symbolu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí, `TRUE` zda jsou data součástí agregace symbolů rozdělených z nadřazeného symbolu. v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Metoda [IDiaSymbol:: get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) je určena `TRUE` pro symbol, který je nadřazeny agregovaným symbolům.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)