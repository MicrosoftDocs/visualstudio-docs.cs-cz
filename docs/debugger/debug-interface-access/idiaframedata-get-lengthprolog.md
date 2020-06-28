---
title: 'IDiaFrameData:: get_lengthProlog | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthProlog method
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9975446cb8c7691f46b6d320f59718d9d87c8440
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467307"
---
# <a name="idiaframedataget_lengthprolog"></a>IDiaFrameData::get_lengthProlog
Načte počet bajtů kódu prologu v bloku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lengthProlog ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí počet bajtů kódu prologu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kód prologu je posloupnost instrukcí, které zachovává Registry, nastavuje stav CPU a vytváří zásobník pro funkci.

## <a name="see-also"></a>Viz také
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)