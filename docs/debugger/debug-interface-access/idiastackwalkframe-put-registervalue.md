---
title: IDiaStackWalkFrame::p ut_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39fc87a6120768eaf1251d81512cbb19f025b7f3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464833"
---
# <a name="idiastackwalkframeput_registervalue"></a>IDiaStackWalkFrame::put_registerValue
Nastaví hodnotu registru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametry
 `index`

pro Hodnota z výčtu [výčtu CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) určující registraci, do které se má zapisovat.

 `NewVal`

pro Nová hodnota registru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [CV_HREG_e – výčet](../../debugger/debug-interface-access/cv-hreg-e.md)