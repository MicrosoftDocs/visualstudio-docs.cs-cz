---
title: marker_series třídy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb199d74ade593d0bc8318c27bc96ffbf70e4dcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194930"
---
# <a name="marker_series-class"></a>marker_series – třída
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Představuje sériový kanál událostí generovaných jedním zprostředkovatelem.  
  
## <a name="syntax"></a>Syntax  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[marker_series::marker_series – konstruktor](../profiling/marker-series-marker-series-constructor.md)|Inicializuje novou instanci `marker_series` třídy.|  
|[marker_series::~marker_series – destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Zničí marker_series objekt a uvolní všechny přidělené prostředky.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[marker_series::is_enabled – metoda](../profiling/marker-series-is-enabled-method.md)|Určuje, zda má kterákoli relace povoleného poskytovatele.|  
|[marker_series::write_alert – metoda](../profiling/marker-series-write-alert-method.md)|Zapíše výstrahu do trasovacího souboru Vizualizátor souběžnosti.|  
|[marker_series::write_flag – metoda](../profiling/marker-series-write-flag-method.md)|Zapíše příznak do trasovacího souboru Vizualizátor souběžnosti.|  
|[marker_series::write_message – metoda](../profiling/marker-series-write-message-method.md)|Zapíše zprávu do trasovacího souboru Vizualizátor souběžnosti.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `marker_series`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkersobj. h  
  
 **Obor názvů:** Concurrency::d odeslání diagnostických  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů diagnostiky](../profiling/diagnostic-namespace.md)
