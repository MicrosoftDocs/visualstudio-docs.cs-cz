---
title: Funkce CvReleaseMarkerSeries – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bfa9952a834110ef0fea36568ea210b637547aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177757"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vydává řady značek. Nepoužívejte objekt řady značek po uvolnění v opačném případě může dojít k chybě aplikace. Neúspěšné vydání řady značek způsobuje nevracení paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMarkerSeries`  
 Adresa proměnné objektu zprostředkovatele Adresa nesmí mít hodnotu NULL, proměnná může mít libovolnou hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK při úspěšném vydání řady značek nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkers. h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)
