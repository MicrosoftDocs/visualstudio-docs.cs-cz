---
title: Funkce Cvcreatemarkerserieswithcodepagea – | Microsoft Docs
description: Podívejte se na referenční informace o funkci Vizualizátor souběžnosti sady SDK Cvcreatemarkerserieswithcodepagea – (knihovna C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 69f4f19df03c4c2f6bb21a5e2262a4a1495adab8
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686152"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Cvcreatemarkerserieswithcodepagea – – funkce
Vytvoří řady značek pro daného zprostředkovatele a zadanou znakovou stránku. Tato funkce se dá použít k určení znakové stránky explicitně pro text zapsaný pomocí funkcí rozhraní API značek ANSI. Nastavení znakové stránky může být užitečné v případě, že je trasování zachyceno a následně analyzováno na různých počítačích s různými místními prostředími nebo jazyky. Ve výchozím nastavení se používá znaková stránka vrácená funkcí GetACP ().

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
 `pProvider` Objekt poskytovatele byl dříve inicializován nástrojem CvInitProvider –. Nemůže mít hodnotu NULL.

 `pSeriesName` Název řady značek Nemůže mít hodnotu NULL, ale je povolen prázdný řetězec.

 `nTextCodePage` Platná znaková stránka.

 `ppMarkerSeries` Adresa výstupní proměnné, která bude ukládat kontext řady značek. Nemůže mít hodnotu NULL.

## <a name="return-value"></a>Vrácená hodnota
 S_OK při úspěšném vytvoření řady značek nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers. h*

## <a name="see-also"></a>Viz také
- [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)