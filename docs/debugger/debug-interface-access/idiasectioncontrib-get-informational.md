---
title: 'IDiaSectionContrib:: get_informational | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d804ef0caa2f6fed3ef33e64f97e51fd81e466ec
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466250"
---
# <a name="idiasectioncontribget_informational"></a>IDiaSectionContrib::get_informational
Načte příznak označující, zda oddíl obsahuje komentáře nebo podobné informace.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_informational(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda oddíl obsahuje komentáře nebo jiné informace. v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Oddíl. direktiva obvykle obsahuje informace.

## <a name="see-also"></a>Viz také
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)