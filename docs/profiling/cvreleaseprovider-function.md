---
title: Funkce Cvreleaseprovider – | Microsoft Docs
description: Podívejte se na referenční informace o funkci Vizualizátor souběžnosti sady SDK Cvreleaseprovider – (knihovna C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae363f1909f169d2d5dc4004a79cfe3c2919bdf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948228"
---
# <a name="cvreleaseprovider-function"></a>Cvreleaseprovider – – funkce
Vydává poskytovatele značek. Uvolnění poskytovatele značek nebude mít vliv na dříve vytvořenou řadu označení tohoto poskytovatele. Řady značek musí být vydány samostatně voláním CvReleaseMarkerSeries –. Selhání poskytovatele Release způsobuje nevracení paměti.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametry
 `pProvider` Kontext poskytovatele. Nemůže mít hodnotu NULL.

## <a name="return-value"></a>Návratová hodnota
 S_OK při úspěšném vydání poskytovatele nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers. h*

## <a name="see-also"></a>Viz také
- [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)