---
title: Funkce CvCreateMarkerSeries | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb3ef4d928aaac57f39a48e5be212c1148ef58eb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552678"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries
Vytvoří řadu značek pro daného zprostředkovatele.

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
 `pProvider`Objekt zprostředkovatele dříve inicializován cvInitProvider. Nemůže být null.

 `pSeriesName`Název řady značek. Nemůže být NULL, ale prázdný řetězec je povolen.

 `ppMarkerSeries`Adresa výstupní proměnné, která bude ukládat kontext řady značek. Nemůže být null.

## <a name="return-value"></a>Návratová hodnota
 S_OK, kdy je řada značek úspěšně vytvořena, nebo kód chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte následující/neúspěšná makra.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Viz také
- [Odkaz na knihovnu C++](../profiling/cpp-library-reference.md)