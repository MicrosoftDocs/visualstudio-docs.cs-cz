---
title: 'IDiaStackWalkHelper:: get_registerValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfb3e219012effe47a2352f7c22c6cf51b4617f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741406"
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

pro Hodnota z výčtu [výčtu CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) , která určuje, ze kterého registru se má získat hodnota.

 `pRetVal`

mimo Vrátí aktuální hodnotu registru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Navzdory velikosti parametru `pRetVal` by implementace měla ukládat pouze to, co registr obvykle uchovává. Například 8bitový registr obsahuje pouze nejnižší 8 bitů dané hodnoty. Tato 16bitová hodnota je rozšířena na 64-bity při návratu z této metody.

## <a name="see-also"></a>Viz také:
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e – výčet](../../debugger/debug-interface-access/cv-hreg-e.md)