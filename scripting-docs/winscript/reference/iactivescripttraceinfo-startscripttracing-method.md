---
title: Iactivescripttraceinfo::startscripttracing – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e999ad0d40f4d832330fee6db17b64ae9da50f08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793563"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing – metoda
Spustí skript trasování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parametry  
 `pSiteTraceInfo`  
 Ukazatel na iactivescriptsitetraceinfo – hostitele.  
  
 `guidContextId`  
 Identifikátor GUID kontextu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty pro tuto metodu jsou následující:  
  
1.  S_OK: Úspěch.  
  
2.  E_POINTER: `pSiteTraceInfo` je NULOVÝ ukazatel.  
  
3.  E_NOTIMPL: Není implementováno.