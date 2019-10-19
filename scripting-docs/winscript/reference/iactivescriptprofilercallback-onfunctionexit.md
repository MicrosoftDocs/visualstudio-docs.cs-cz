---
title: 'Iactivescriptprofilercallback –:: OnFunctionExit | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571679"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Upozorní objekt profileru, že skriptovací modul dokončil provádění volání funkce, které není voláním do model DOM (Document Object Model) (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 pro Jedinečné ID skriptu, jehož funkce je součástí. Toto ID přiřadí skriptovací stroj.  
  
 `functionId`  
 pro Jedinečné ID funkce Toto ID přiřadí skriptovací stroj.  
  
## <a name="return-value"></a>Návratová hodnota  
 Skriptovací stroj ignoruje vrácenou hodnotu této metody.  
  
## <a name="remarks"></a>Poznámky  
 V případě volání DOM skriptovací modul volá [iactivescriptprofilercallback2 –:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) namísto `IActiveScriptProfilerCallback::OnFunctionExit`. Důvodem je velký počet jedinečných metod a vlastností v modelu DOM.  
  
## <a name="see-also"></a>Viz také:  
 [Iactivescriptprofilercallback –:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [IActiveScriptProfilerCallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)