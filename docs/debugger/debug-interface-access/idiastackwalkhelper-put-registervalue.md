---
description: IDiaStackWalkHelper::p ut_registerValue nastavuje hodnotu registru.
title: IDiaStackWalkHelper::p ut_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdc66faea9537759e9754ce799339175db585673
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156823"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
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

## <a name="remarks"></a>Poznámky
 Navzdory velikosti hodnoty by implementace měla ukládat pouze to, co registr obvykle uchovává. Například 8bitové Registry by obsahovaly pouze nejnižší 8 bitů dané hodnoty.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e – výčet](../../debugger/debug-interface-access/cv-hreg-e.md)
