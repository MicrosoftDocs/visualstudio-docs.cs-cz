---
title: 'IDiaStackFrame:: get_registerValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f11d99a3e3a8a78b6c8152dd94a28f27d800772
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863940"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Načte hodnotu zadaného registru, jak je uloženo v rámci bloku zásobníku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `registerIndex`

pro Jedna z hodnot výčtu [CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) výčtu.

 `pRetVal`

mimo Hodnota uložená v registru

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e – výčet](../../debugger/debug-interface-access/cv-hreg-e.md)