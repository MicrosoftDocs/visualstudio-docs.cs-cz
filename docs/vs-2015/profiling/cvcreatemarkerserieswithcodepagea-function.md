---
title: Funkce Cvcreatemarkerserieswithcodepagea – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 635a872372ab775eceb00854a616884f3fc19fef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155534"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří řady značek pro daného zprostředkovatele a zadanou znakovou stránku. Tato funkce se dá použít k určení znakové stránky explicitně pro text zapsaný pomocí funkcí rozhraní API značek ANSI. Nastavení znakové stránky může být užitečné v případě, že je trasování zachyceno a následně analyzováno na různých počítačích s různými místními prostředími nebo jazyky. Ve výchozím nastavení se používá znaková stránka vrácená funkcí GetACP ().  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Objekt poskytovatele byl dříve inicializován nástrojem CvInitProvider –. Nemůže mít hodnotu NULL.  
  
 `pSeriesName`  
 Název řady značek Nemůže mít hodnotu NULL, ale je povolen prázdný řetězec.  
  
 `nTextCodePage`  
 Platná znaková stránka.  
  
 `ppMarkerSeries`  
 Adresa výstupní proměnné, která bude ukládat kontext řady značek. Nemůže mít hodnotu NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK při úspěšném vytvoření řady značek nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkers. h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)
