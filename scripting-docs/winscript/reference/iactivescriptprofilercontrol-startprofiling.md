---
title: 'IActiveScriptProfilerControl:: StartProfiling | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfc59dd43ac3eed433f92af2cdd0aefe40392c4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571569"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Spustí profilování v skriptovacím stroji. Skriptovací stroj vytvoří instanci objektu profileru tak, že vyvolá volání funkce [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsidProfilerObject`  
 pro Identifikátor třídy (CLSID) objektu profileru, který má být vytvořen.  
  
 `dwEventMask`  
 pro Bitová maska o velikosti 4 bajty, která určuje typy událostí. Bity jsou definované ve [výčtu PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 pro Hodnota 4 bajty, která je předána objektu profileru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Profilace je už povolená.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerControl – rozhraní](../../winscript/reference/iactivescriptprofilercontrol-interface.md)