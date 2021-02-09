---
title: 'IDiaEnumFrameData:: frameByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 48bffc8e07ede412c9d33176fdaf29ba85ba1f0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856871"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Vrátí rámec podle virtuální adresy (VA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parametry
 virtualAddress

pro VA snímku zájmu.

 rámec

mimo Vrátí objekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , který představuje rámec obsahující poskytnutou adresu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda žádná data rámce neodpovídají zadané adrese. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)