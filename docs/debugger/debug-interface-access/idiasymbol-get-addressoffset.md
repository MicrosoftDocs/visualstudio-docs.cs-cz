---
title: 'IDiaSymbol:: get_addressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e5d5c865ca503890f3f29df44bcd65dd10343bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854596"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
Načte odkládací část umístění adresy. Použijte v případě, že je [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) nastaven na hodnotu `LocIsStatic` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí odkládací část umístění adresy.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 U statických členů umístěných v externí knihovně DLL může být posun vrácený touto metodou 0, protože tato metoda spoléhá na získání virtuální adresy člena. Virtuální adresy jsou platné pouze v případě, že metoda [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) v rozhraní [IDiaSession](../../debugger/debug-interface-access/idiasession.md) byla volána s nenulovým parametrem, který určuje adresu načtení knihovny DLL.

 Chcete-li získat část adresy, zavolejte metodu [IDiaSymbol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) .

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)