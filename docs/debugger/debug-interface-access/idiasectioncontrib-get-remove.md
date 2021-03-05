---
description: Načte příznak, který označuje, zda je oddíl odebrán před tím, než se stane součástí obrázku v paměti.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf345506988ed2a6954bf4bdbce5e7b7dad1afa9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147910"
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
