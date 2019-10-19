---
title: 'IActiveScriptProfilerControl:: StopProfiling | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StopProfiling
apilocation:
- scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5900678093d57b3c995ac3bca8464ccd612fb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571548"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Zastaví profilování v skriptovacím stroji. Tato metoda volá [iactivescriptprofilercallback –:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) objektu profileru a pak ho uvolní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hrShutdownReason`  
 pro Hodnota HRESULT, která má být předána jako parametr metodě [iactivescriptprofilercallback –:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) objektu profileru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilace není povolená.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerControl – rozhraní](../../winscript/reference/iactivescriptprofilercontrol-interface.md)