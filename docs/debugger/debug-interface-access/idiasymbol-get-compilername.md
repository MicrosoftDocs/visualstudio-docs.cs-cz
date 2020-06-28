---
title: 'IDiaSymbol:: get_compilerName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49491d2d9934a20e9d40c0dcd5aadeed3ef27ca7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464077"
---
# <a name="idiasymbolget_compilername"></a>IDiaSymbol::get_compilerName
Vrátí název kompilátoru, který se používá ke generování [kompilantu](../../debugger/debug-interface-access/compiland.md).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_compilerName (
   BSTR *pName
);
```

#### <a name="parameters"></a>Parametry
 `pName`Ukazatel na objekt BSTR, který bude obsahovat název Unicode kompilátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)