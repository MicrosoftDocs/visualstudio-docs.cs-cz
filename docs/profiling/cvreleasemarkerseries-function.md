---
title: Cvreleasemarkerseries – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27c5bbc5d47972a4829c4e46f6aafdcf8ee76fad
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749356"
---
# <a name="cvreleasemarkerseries-function"></a>Cvreleasemarkerseries – funkce
Uvolní řady značky. Nepoužívejte značky řady objektu po vydání aplikace jinak může dojít k selhání. Chyby k uvolnění značky řady způsobí, že nevrácenou pamětí.  
  
## <a name="syntax"></a>Syntaxe  
  
```C  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMarkerSeries`  
 Adresa poskytovatele objektová proměnná. Adresa nesmí být NULL, proměnná může mít žádnou hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK při řady značky úspěšně vydání nebo kód chyby v případě, že existuje byly všechny chyby. Makra úspěšné nebo NEÚSPĚŠNÉ použijte ke kontrole chybový stav.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** *cvmarkers.h*  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace knihoven jazyka C++](../profiling/cpp-library-reference.md)