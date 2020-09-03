---
title: Funkce Cvwriteflag – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteFlagExVA
- cvmarkers/CvWriteFlagExW
- cvmarkers/CvWriteFlagExVW
- cvmarkers/CvWriteFlagExA
helpviewer_keywords:
- CvWriteFlagExW method
- CvWriteFlagExVA method
- CvWriteFlagExA method
- CvWriteFlagExVW method
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bea5e2acea9a89c5a3b2fdfba441530a74ad8515
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177734"
---
# <a name="cvwriteflag-function"></a>CvWriteFlag – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapíše příznak do trasovacího souboru Vizualizátor souběžnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Parametry  
 `argList`  
 Seznam argumentů  
  
 `category`  
 Kategorií.  
  
 `level`  
 Úroveň důležitosti.  
  
 `pMarkerSeries`  
 Platný kontext řady značek Nemůže mít hodnotu NULL.  
  
 `pMessage`  
 Řetězec formátu zprávy Nemůže mít hodnotu NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK při úspěšném zápisu zprávy Kód chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkers. h  
  
 **Kódování Unicode:** CvWriteFlagExW, CvWriteFlagExVW  
  
 <strong>ANSI:</strong> CvWriteFlagExA, CvWriteFlagExVA  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)
