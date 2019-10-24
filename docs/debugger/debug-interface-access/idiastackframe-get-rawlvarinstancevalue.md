---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741638"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Tato metoda načte hodnotu zadané místní proměnné jako nezpracované bajty.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Parametry
 `pInstance`

pro Objekt `IDiaLVarInstance` reprezentující instanci lokální proměnné pro získání hodnoty pro.

 `cbDataMax`

pro Maximální počet bajtů ve vyrovnávací paměti, na které ukazuje `pbData`. Může to být maximálně 8 bajtů (`sizeof(ULONGLONG)`).

 `pcbData`

mimo Vrátí skutečný počet bajtů uložených ve vyrovnávací paměti.

 `pbData`

mimo Vyrovnávací paměť, která se má vyplnit daty. Toto nelze `NULL`.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také:
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)