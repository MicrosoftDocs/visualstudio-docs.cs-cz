---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e7216c5878a13b4312d737ae266004d757c24db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864570"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Načte odpovídající názvy řetězců pro dané identifikátory vlastností.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Parametry
 `cpropid`

pro Počet ID vlastností v `rgpropid` .

 `rgpropid`

pro Pole ID vlastností, pro které se mají získat názvy ( `PROPID` je definováno v WTypes. h jako `ULONG` ).

 `rglpwstrName`

[in, out] Pole názvů vlastností pro zadaná ID vlastností Pole musí být předem přiděleno pro uchování požadovaného počtu názvů vlastností a musí být schopno uchovávat nejméně `cpropid``BSTR` řetězce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Názvy vrácených vlastností musí být uvolněny (voláním `SysFreeString` funkce), pokud už je nepotřebujete.

## <a name="see-also"></a>Viz také
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)