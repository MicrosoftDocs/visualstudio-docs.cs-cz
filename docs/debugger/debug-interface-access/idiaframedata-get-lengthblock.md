---
description: Načte délku bloku kódu popsaného rámcem v bajtech.
title: 'IDiaFrameData:: get_lengthBlock | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthBlock method
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 824c224fa84318f6bd6fd2c590992cff89839af0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148568"
---
# <a name="idiaframedataget_lengthblock"></a>IDiaFrameData::get_lengthBlock
Načte délku bloku kódu popsaného rámcem v bajtech.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lengthBlock ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí počet bajtů kódu v rámci.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnota vrácená touto metodou se obvykle používá ve výkladu řetězce programu (viz metoda [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) pro definici řetězce programu).

## <a name="see-also"></a>Viz také
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
