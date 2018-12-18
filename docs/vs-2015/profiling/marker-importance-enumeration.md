---
title: marker_importance – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32e57a9463e6c6966c215066fd470b62596f5481
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756859"
---
# <a name="markerimportance-enumeration"></a>marker_importance – výčet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Představuje úroveň důležitosti značek Vizualizátor souběžnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`critical_importance`|Určuje, že má značku stěžejní význam.|  
|`high_importance`|Určuje, že značky má vysokou důležitostí.|  
|`low_importance`|Určuje, zda má značku s nízkou důležitostí.|  
|`normal_importance`|Určuje, že značky má normální význam.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::Diagnostic –  
  
## <a name="see-also"></a>Viz také  
 [diagnostic – obor názvů](../profiling/diagnostic-namespace.md)



