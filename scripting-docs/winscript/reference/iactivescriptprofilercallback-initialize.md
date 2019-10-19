---
title: 'Iactivescriptprofilercallback –:: Initialize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576444"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Volá se, aby se inicializoval objekt profileru, když se v skriptovacím modulu spustí profilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwContext`  
 pro Hodnota 4 bajty, která je předána do [IActiveScriptProfilerControl:: StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud metoda nemůže inicializovat objekt profileru, měl by vrátit chybu HRESULT, aby upozornil skriptovací modul. V takovém případě skriptovací modul by měl přímo volat metodu [iactivescriptprofilercallback –:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), předávat HRESULT v parametru a pak uvolnit objekt profileru.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerCallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)