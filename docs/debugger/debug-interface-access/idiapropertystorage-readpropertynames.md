---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742874"
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

pro Počet ID vlastností v `rgpropid`.

 `rgpropid`

pro Pole ID vlastností, pro které se mají získat názvy (`PROPID` jsou definovány v WTypes. h jako `ULONG`).

 `rglpwstrName`

[in, out] Pole názvů vlastností pro zadaná ID vlastností Pole musí být předem přiděleno pro uchování požadovaného počtu názvů vlastností a musí být schopné uchovávat alespoň `cpropid``BSTR` řetězce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Názvy vrácených vlastností musí být uvolněny (voláním funkce `SysFreeString`), pokud už je nepotřebujete.

## <a name="see-also"></a>Viz také:
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)