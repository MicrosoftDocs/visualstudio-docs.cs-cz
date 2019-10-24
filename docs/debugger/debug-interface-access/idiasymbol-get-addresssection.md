---
title: 'IDiaSymbol:: get_addressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a468fe6ee8a8d7d00bb2e6c261d50919a1dd764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741080"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Načte část umístění adresy. Použijte, pokud je [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) nastavený na `LocIsStatic`.

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
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Pro statické členy nacházející se v externí knihovně DLL může být oddíl vrácený touto metodou 0, protože tato metoda spoléhá na získání virtuální adresy člena. Virtuální adresy jsou platné pouze v případě, že metoda [IDiaSession::P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) v rozhraní [IDiaSession](../../debugger/debug-interface-access/idiasession.md) byla volána s nenulovým parametrem, který určuje adresu načtení knihovny DLL.

 Chcete-li získat posunovou část adresy, zavolejte metodu [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) .

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Znění|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také:
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)