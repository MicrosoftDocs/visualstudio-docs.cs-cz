---
description: Načte typ ukazatele virtuální základní tabulky.
title: 'IDiaSymbol:: get_virtualBaseTableType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67affafd1984f811432a0b69fdcdfec0521e377
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155514"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Načte typ ukazatele virtuální základní tabulky.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`pRetVal`|mimo Vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který určuje typ základní tabulky.|

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Ukazatel virtuální základní tabulky ( `vbtptr` ) je skrytý ukazatel v tabulce [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable, který zpracovává dědičnost z virtuálních základních tříd. `vbtptr`Může mít různé velikosti v závislosti na zděděných třídách.

 Tato metoda vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který lze použít k určení velikosti vbtptr.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
