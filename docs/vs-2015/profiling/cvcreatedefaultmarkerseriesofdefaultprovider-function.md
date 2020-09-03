---
title: Funkce Cvcreatedefaultmarkerseriesofdefaultprovider – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb0ab16dcd7e42a496317f4e7589bafdbdaf83dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161999"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří výchozí řadu značek výchozího zprostředkovatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProvider`  
 Adresa proměnné objektu zprostředkovatele Adresa nesmí mít hodnotu NULL, proměnná může mít libovolnou hodnotu.  
  
 `ppMarkerSeries`  
 Adresa proměnné objektu řady značek Adresa nesmí mít hodnotu NULL, proměnná může mít libovolnou hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK při úspěšném vytvoření poskytovatele i řady značek nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkers. h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)
