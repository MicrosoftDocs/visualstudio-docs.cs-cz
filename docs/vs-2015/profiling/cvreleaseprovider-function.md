---
title: Funkce Cvreleaseprovider – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d5e611c2a964fcbb78a387a09989436e672ecd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551231"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vydává poskytovatele značek. Uvolnění poskytovatele značek nebude mít vliv na dříve vytvořenou řadu označení tohoto poskytovatele. Řady značek musí být vydány samostatně voláním CvReleaseMarkerSeries –. Selhání poskytovatele Release způsobuje nevracení paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Kontext poskytovatele. Nemůže mít hodnotu NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK při úspěšném vydání poskytovatele nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkers. h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)
