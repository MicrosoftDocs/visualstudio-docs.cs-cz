---
title: Funkce CvCreateMarkerSeriesWithCodePageA | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7e540e56ce0e97ac2c6aa2e42012569f9e4f272
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553068"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA
Vytvoří řadu značek pro daného zprostředkovatele a zadanou znakovou stránku. Tuto funkci lze použít k určení znakové stránky explicitně pro text napsaný funkcemi ANSI markerAPI. Nastavení znakové stránky může být užitečné v případě, že trasování je zachycena a poté analyzována na různých počítačích s různými národními prostředími / jazyky. Ve výchozím nastavení se používá znaková stránka vrácená funkcí GetACP().

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `pProvider`Objekt zprostředkovatele dříve inicializován cvInitProvider. Nemůže být null.

 `pSeriesName`Název řady značek. Nemůže být NULL, ale prázdný řetězec je povolen.

 `nTextCodePage`Platná znaková stránka.

 `ppMarkerSeries`Adresa výstupní proměnné, která bude ukládat kontext řady značek. Nemůže být null.

## <a name="return-value"></a>Návratová hodnota
 S_OK, kdy je řada značek úspěšně vytvořena, nebo kód chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte následující/neúspěšná makra.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers.h*

## <a name="see-also"></a>Viz také
- [Odkaz na knihovnu C++](../profiling/cpp-library-reference.md)