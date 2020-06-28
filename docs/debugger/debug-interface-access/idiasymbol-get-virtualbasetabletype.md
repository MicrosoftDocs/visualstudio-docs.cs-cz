---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 858f149abb0bec444c43ea706e638def4ff930ce
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461439"
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