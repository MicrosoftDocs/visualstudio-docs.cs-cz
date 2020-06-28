---
title: 'IDiaSymbol:: get_addressTaken | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b62a848d70b59a1764220c806123b0edd03edf2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464350"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
Načte příznak, který označuje, zda jiný symbol odkazuje na adresu tohoto symbolu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí `TRUE` , zda odkaz na tuto adresu odkazuje na jiný symbol. v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="example"></a>Příklad
 V následujícím příkladu odkazuje na `B` `A` . Proto se `A` Metoda symbolu `get_addressTaken` vrátí `TRUE` .

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)