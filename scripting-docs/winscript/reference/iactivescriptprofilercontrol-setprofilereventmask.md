---
title: IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b20b5410af7e48f1b9dadb937e794c1941e74df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793554"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Nastaví 4bajtový bitová maska, která určuje typy událostí, které by měla vyvolat skriptovacího stroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwEventMask`  
 [v] 4bajtový bitová maska, která určuje typy událostí. Službu bits jsou definovány v [PROFILER_EVENT_MASK – výčet](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilace není povoleno.|  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptprofilercontrol – rozhraní](../../winscript/reference/iactivescriptprofilercontrol-interface.md)