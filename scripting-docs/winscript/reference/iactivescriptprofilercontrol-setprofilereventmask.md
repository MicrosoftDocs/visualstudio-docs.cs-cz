---
title: 'IActiveScriptProfilerControl:: SetProfilerEventMask | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a4162cf2e5325bfb41bce9c3a47a52b1b36d74f2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571590"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Nastavuje 4 bajtovou bitovou masku, která určuje typy událostí, které by měl skriptovací stroj vyvolat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwEventMask`  
 pro Bitová maska o velikosti 4 bajty, která určuje typy událostí. Bity jsou definované ve [výčtu PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilace není povolená.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerControl – rozhraní](../../winscript/reference/iactivescriptprofilercontrol-interface.md)