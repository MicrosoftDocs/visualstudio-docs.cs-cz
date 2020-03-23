---
title: Funkce CvCreateDefaultMarkerSeriesOfDefaultProvider | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a13174b2991b7c69535a6d1910f761890397818
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552691"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider
Vytvoří výchozí řadu značek výchozího zprostředkovatele.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `ppProvider`Adresa proměnné objektu zprostředkovatele. Adresa nemůže být NULL, proměnná může mít libovolnou hodnotu.

 `ppMarkerSeries`Adresa proměnné objektu řady značek. Adresa nemůže být NULL, proměnná může mít libovolnou hodnotu.

## <a name="return-value"></a>Návratová hodnota
 S_OK, kdy jsou úspěšně vytvořeny řady zprostředkovatelů a značek, nebo kód chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte následující/neúspěšná makra.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers.h*

## <a name="see-also"></a>Viz také
- [Odkaz na knihovnu C++](../profiling/cpp-library-reference.md)