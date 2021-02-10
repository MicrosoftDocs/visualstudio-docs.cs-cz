---
title: Funkce Cvcreatemarkerseries – | Microsoft Docs
description: Podívejte se na referenční informace o funkci Vizualizátor souběžnosti sady SDK Cvcreatemarkerseries – (knihovna C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941031"
---
# <a name="cvcreatemarkerseries-function"></a>Cvcreatemarkerseries – – funkce
Vytvoří řady značek pro daného zprostředkovatele.

## <a name="syntax"></a>Syntaxe

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>Parametry
 `pProvider` Objekt poskytovatele byl dříve inicializován nástrojem CvInitProvider –. Nemůže mít hodnotu NULL.

 `pSeriesName` Název řady značek Nemůže mít hodnotu NULL, ale je povolen prázdný řetězec.

 `ppMarkerSeries` Adresa výstupní proměnné, která bude ukládat kontext řady značek. Nemůže mít hodnotu NULL.

## <a name="return-value"></a>Vrácená hodnota
 S_OK při úspěšném vytvoření řady značek nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers. h*

 **Kódování Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Viz také
- [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)