---
title: 'marker_series:: marker_series konstruktor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b42058e0501612acbf454df725a9f1631489d26e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155286"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series::marker_series – konstruktor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicializuje novou instanci `marker_series` třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_SeriesName`  
 Název řady, která se má vytvořit.  
  
 `_ProviderGuid`  
 Identifikátor GUID zprostředkovatele řad.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkersobj. h  
  
 **Obor názvů:** Concurrency::d odeslání diagnostických  
  
## <a name="see-also"></a>Viz také  
 [marker_series – třída](../profiling/marker-series-class.md)
