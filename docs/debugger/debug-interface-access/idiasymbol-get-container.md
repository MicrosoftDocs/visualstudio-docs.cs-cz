---
description: Tato funkce načte ukazatel na symbol představující nadřazený nebo kontejner tohoto symbolu.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 724127e50708585613175b0f5773f231f1b33944
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156382"
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
