---
title: Funkce CvInitProvider | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a97be63cd782397e984fd8dbce7da844efa07540
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552664"
---
# <a name="cvinitprovider-function"></a>CvInitProvider
Inicializuje zprostředkovatele značky. Musí být volána před všechny ostatní funkce souběžnosti Vizulizátor SDK.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametry
 `pGuid`Identifikátor GUID zprostředkovatele. Nemůže být null.

 `ppProvider`Adresa výstupní proměnné, která bude ukládat kontext zprostředkovatele. Nemůže být null.

## <a name="return-value"></a>Návratová hodnota
 S_OK, kdy je zprostředkovatel úspěšně inicializován, nebo kód chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte následující/neúspěšná makra.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers.h*

## <a name="see-also"></a>Viz také
- [Odkaz na knihovnu C++](../profiling/cpp-library-reference.md)