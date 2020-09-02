---
title: Výčet marker_importance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198392"
---
# <a name="marker_importance-enumeration"></a>marker_importance – výčet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Představuje úroveň důležitosti značky Vizualizátor souběžnosti.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`critical_importance`|Určuje, že značka má kritickou důležitost.|  
|`high_importance`|Určuje, že značka má velkou důležitost.|  
|`low_importance`|Určuje, že značka má nízkou důležitost.|  
|`normal_importance`|Určuje, že má značka normální důležitost.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkersobj. h  
  
 **Obor názvů:** Concurrency::d odeslání diagnostických  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů diagnostiky](../profiling/diagnostic-namespace.md)
