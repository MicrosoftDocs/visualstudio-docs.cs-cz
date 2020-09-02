---
title: 'IDiaSymbol:: get_hasManagedCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasManagedCode method
ms.assetid: e40f82f5-88fe-4a9b-b594-3605f42773ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e4ce3326e6922227b83a12b21b6fc2aa2f9ce81e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463692"
---
# <a name="idiasymbolget_hasmanagedcode"></a>IDiaSymbol::get_hasManagedCode
Načte příznak označující, zda modul obsahuje spravovaný kód.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasManagedCode(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí `TRUE` , zda modul obsahuje spravovaný kód. v opačném případě vrátí `FALSE` kód nespravovaný kód.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je k dispozici z `SymTagCompilandDetails` typu symbolu (viz [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)