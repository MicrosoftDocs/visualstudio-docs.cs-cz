---
title: 'IDiaSectionContrib:: get_remove | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_remove method
ms.assetid: fd30ab7b-022b-4402-a42a-2d38e274c1b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7d98260678af245fbc5a17593670a2471e9a488
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466110"
---
# <a name="idiasectioncontribget_remove"></a>IDiaSectionContrib::get_remove
Načte příznak, který označuje, zda je oddíl odebrán před tím, než se stane součástí obrázku v paměti.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_remove ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí `TRUE` , zda se oddíl nepřidá do bitové kopie v paměti; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)