---
title: 'IDiaFrameData:: get_addressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_addressOffset method
ms.assetid: b68e2e68-6483-4936-bf97-1b0a13cb75e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b48e1a0f5f0655c80e501740eae5fc4152f998a4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467440"
---
# <a name="idiaframedataget_addressoffset"></a>IDiaFrameData::get_addressOffset
Načte část s odsazením kódu pro rámec.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí část adresy kódu pro rámec.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)