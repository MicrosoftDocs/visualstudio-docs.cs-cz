---
title: 'IDiaStackFrame:: get_size | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_size method
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 238dfd6195b2f7538978a46df6a36d21b6c19250
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464959"
---
# <a name="idiastackframeget_size"></a>IDiaStackFrame::get_size
Načte velikost rámce zásobníku v bajtech.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_size ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí velikost rámce zásobníku v bajtech.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí hodnotu, `S_FALSE` Pokud vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)