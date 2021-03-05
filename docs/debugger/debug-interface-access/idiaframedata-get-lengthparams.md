---
description: 'IDiaFrameData:: get_lengthParams načte počet bajtů parametrů přesunutých do zásobníku.'
title: 'IDiaFrameData:: get_lengthParams | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthParams method
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f686095ab06097ff72692c988888e1e2954d3796
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157733"
---
# <a name="idiaframedataget_lengthparams"></a>IDiaFrameData::get_lengthParams
Načte počet bajtů parametrů přesunutých do zásobníku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí počet bajtů parametrů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnota vrácená touto metodou se obvykle používá ve výkladu řetězce programu (viz metoda [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) pro definici řetězce programu).

## <a name="see-also"></a>Viz také
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
