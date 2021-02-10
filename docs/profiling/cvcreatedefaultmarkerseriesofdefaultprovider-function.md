---
title: Funkce Cvcreatedefaultmarkerseriesofdefaultprovider – | Microsoft Docs
description: Podívejte se na referenční informace o funkci Vizualizátor souběžnosti sady SDK Cvcreatedefaultmarkerseriesofdefaultprovider – (knihovna C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32d7730d36f7e99a2557e764c2adb92862515e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941044"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Cvcreatedefaultmarkerseriesofdefaultprovider – – funkce
Vytvoří výchozí řadu značek výchozího zprostředkovatele.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `ppProvider` Adresa proměnné objektu zprostředkovatele Adresa nesmí mít hodnotu NULL, proměnná může mít libovolnou hodnotu.

 `ppMarkerSeries` Adresa proměnné objektu řady značek Adresa nesmí mít hodnotu NULL, proměnná může mít libovolnou hodnotu.

## <a name="return-value"></a>Vrácená hodnota
 S_OK při úspěšném vytvoření poskytovatele i řady značek nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers. h*

## <a name="see-also"></a>Viz také
- [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)