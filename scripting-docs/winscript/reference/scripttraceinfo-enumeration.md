---
title: SCRIPTTRACEINFO – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1902b290a8024679cef12d503e94de4923defb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796350"
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO – výčet
Představuje skriptu událost, která jsou trasovány. Používány [iactivescriptsitetraceinfo::sendscripttraceinfo – metoda](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Hodnoty výčtu  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|Spuštění skriptu.|  
|SCRIPTTRACEINFO_SCRIPTEND|Konec skriptu.|  
|SCRIPTTRACEINFO_COMCALLSTART|Spuštění volání COM.|  
|SCRIPTTRACEINFO_COMCALLEND|Konec volání COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|Spuštění vytvoření objektu.|  
|SCRIPTTRACEINFO_CREATEOBJEND|Konec vytvoření objektu.|  
|SCRIPTTRACEINFO_GETOBJSTART|Spuštění GetObject volání.|  
|SCRIPTTRACEINFO_GETOBJEND|Konec GetObject volání.|