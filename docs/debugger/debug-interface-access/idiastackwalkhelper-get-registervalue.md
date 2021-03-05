---
description: 'IDiaStackWalkHelper:: get_registerValue načte hodnotu registru.'
title: 'IDiaStackWalkHelper:: get_registerValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa87529f90b20d7d9099dd76e294e406ae0c7a08
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161178"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
Načte hodnotu registru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `index`

pro Hodnota z výčtu [výčtu CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) určující, ze kterého registru se má získat hodnota.

 `pRetVal`

mimo Vrátí aktuální hodnotu registru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Navzdory velikosti `pRetVal` parametru by implementace měla ukládat pouze to, co registr obvykle uchovává. Například 8bitový registr obsahuje pouze nejnižší 8 bitů dané hodnoty. Tato 16bitová hodnota je rozšířena na 64-bity při návratu z této metody.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e – výčet](../../debugger/debug-interface-access/cv-hreg-e.md)
