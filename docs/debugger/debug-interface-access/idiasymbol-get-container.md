---
title: 'IDiaSymbol:: get_container | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62bb2f29d737aeb09cc228038be96480922e204c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464028"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
Tato funkce načte ukazatel na symbol představující nadřazený nebo kontejner tohoto symbolu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí ukazatel na `IDiaSymbol` obsahující informace o kontejneru tohoto symbolu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí S_FALSE nebo kód chyby.

> [!NOTE]
> Návratová hodnota S_FALSE znamená, že vlastnost není k dispozici pro symbol.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)