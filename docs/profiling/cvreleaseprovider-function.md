---
title: Funkce CvReleaseProvider | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008b7476290558c098b2241fde5c9b209933a0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62974043"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider
Uvolní zprostředkovatele značky. Uvolnění zprostředkovatele značky neovlivní dříve vytvořené řady značek tohoto zprostředkovatele. Marker série musí být vydána samostatně cvReleaseMarkerSeries volání. Selhání uvolnění zprostředkovatele způsobí nevracení paměti.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametry
 `pProvider`Kontext zprostředkovatele. Nemůže být null.

## <a name="return-value"></a>Návratová hodnota
 S_OK, když je zprostředkovatel úspěšně uvolněna nebo kód chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte následující/neúspěšná makra.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers.h*

## <a name="see-also"></a>Viz také
- [Odkaz na knihovnu C++](../profiling/cpp-library-reference.md)