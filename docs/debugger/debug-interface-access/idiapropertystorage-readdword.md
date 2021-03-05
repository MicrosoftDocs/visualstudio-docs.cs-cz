---
description: Přečte hodnoty DWORD v sadě vlastností.
title: 'IDiaPropertyStorage:: ReadDWORD | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70eb083c3b4469037195334a0bbfa3784462c89e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148162"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Přečte `DWORD` hodnoty v sadě vlastností.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parametry
 `id`

pro Identifikátor vlastnosti, která má být načtena ( `PROPID` je definována v WTypes. h jako `ULONG` ).

 `pValue`

mimo Vrátí hodnotu vlastnosti.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Vrátí, `E_INVALIDARG` zda vlastnost není typu `DWORD` .

## <a name="remarks"></a>Poznámky
 Objekt `DWORD` je definován systémem Windows jako 32-bit unsigned integer.

## <a name="see-also"></a>Viz také
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
