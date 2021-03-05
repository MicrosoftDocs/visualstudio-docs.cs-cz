---
description: Tato metoda načte hodnotu zadané místní proměnné jako nezpracované bajty.
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dc7bc12fe8fd38fc02b6794b2026bce328d95511
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147441"
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

pro `IDiaLVarInstance` Objekt představující instanci lokální proměnné pro získání hodnoty pro.

 `cbDataMax`

pro Maximální počet bajtů ve vyrovnávací paměti, na které ukazuje `pbData` . Může to být maximálně 8 bajtů ( `sizeof(ULONGLONG)` ).

 `pcbData`

mimo Vrátí skutečný počet bajtů uložených ve vyrovnávací paměti.

 `pbData`

mimo Vyrovnávací paměť, která se má vyplnit daty. To nemůže být `NULL` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
