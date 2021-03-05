---
description: 'IDiaStackFrame:: get_lengthLocals načte počet bajtů místních proměnných vložených v zásobníku.'
title: 'IDiaStackFrame:: get_lengthLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthLocals method
ms.assetid: dbc3e544-578a-4f0b-8d20-f21ad4cbb604
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21bca9962d73bf02deed763fb1c0de49eef5efe8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147483"
---
# <a name="idiastackframeget_lengthlocals"></a>IDiaStackFrame::get_lengthLocals
Načte počet bajtů místních proměnných vložených v zásobníku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lengthLocals ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí počet bajtů místních proměnných.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí hodnotu, `S_FALSE` Pokud vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
