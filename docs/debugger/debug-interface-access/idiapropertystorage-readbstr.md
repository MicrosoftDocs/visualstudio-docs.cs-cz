---
title: 'IDiaPropertyStorage:: Readbstr – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6e87c2ed168a262fc1a12f06fc6a18bcf73e7bc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466593"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Přečte `BSTR` hodnoty v sadě vlastností.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parametry
 `id`

pro Identifikátor vlastnosti, která má být načtena ( `PROPID` je definována v WTypes. h jako `ULONG` ).

 `pValue`

mimo Vrátí hodnotu vlastnosti.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Vrátí, `E_INVALIDARG` zda vlastnost není typu `BSTR` .

## <a name="remarks"></a>Poznámky
 Objekt `BSTR` je definován systémem Windows jako řetězec s velkým počtem znaků zakončený nulou.

## <a name="see-also"></a>Viz také
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)