---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9af9dc5ce1f4cb0eb5c328c90c20184111afd9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793467"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Upozorní profileru objekt, který skriptovacího stroje se chystá provést volání funkce, které není volání do objektu modelu dokumentu (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 [v] Jedinečné ID skript, který je součástí funkce. Toto ID je přiřazena službou skriptovacího stroje.  
  
 `functionId`  
 [v] Jedinečné ID funkce. Toto ID je přiřazena službou skriptovacího stroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota tato metoda je ignorován v skriptovacího stroje.  
  
## <a name="remarks"></a>Poznámky  
 Pro volání DOM skriptovacího stroje volá [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) místo `IActiveScriptProfilerCallback::OnFunctionEnter`. Je to z důvodu velkého počtu jedinečných metody a vlastnosti v modelu DOM.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Iactivescriptprofilercallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)