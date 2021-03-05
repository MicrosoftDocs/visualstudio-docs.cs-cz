---
description: Načte část umístění adresy.
title: 'IDiaSymbol:: get_addressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e0b6554011a29a7b90d1d7c55deefced01b27c3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156585"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Načte část umístění adresy. Použijte v případě, že je [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) nastaven na hodnotu `LocIsStatic` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí část umístění adresy.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Pro statické členy nacházející se v externí knihovně DLL může být oddíl vrácený touto metodou 0, protože tato metoda spoléhá na získání virtuální adresy člena. Virtuální adresy jsou platné pouze v případě, že metoda [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) v rozhraní [IDiaSession](../../debugger/debug-interface-access/idiasession.md) byla volána s nenulovým parametrem, který určuje adresu načtení knihovny DLL.

 Chcete-li získat posunovou část adresy, zavolejte metodu [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) .

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
