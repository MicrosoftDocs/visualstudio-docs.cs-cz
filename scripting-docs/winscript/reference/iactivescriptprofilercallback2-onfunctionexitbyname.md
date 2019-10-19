---
title: 'Iactivescriptprofilercallback2 –:: OnFunctionExitByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571620"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Upozorní objekt profileru, že skriptovací stroj dokončil běh volání funkce model DOM (Document Object Model) (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 pro Název funkce, kterou skriptovací stroj dokončil při běhu.  
  
 `scriptType`  
 pro Typ funkce. Popisy platných hodnot naleznete v tématu [PROFILER_SCRIPT_TYPE Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Skriptovací stroj ignoruje vrácenou hodnotu této metody.  
  
## <a name="remarks"></a>Poznámky  
 Pro volání DOM skriptovací modul volá tuto metodu místo volání metody [iactivescriptprofilercallback –:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Důvodem je velký počet jedinečných metod a vlastností v modelu DOM.  
  
## <a name="see-also"></a>Viz také:  
 [Iactivescriptprofilercallback2 –:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2 – rozhraní](../../winscript/reference/iactivescriptprofilercallback2-interface.md)