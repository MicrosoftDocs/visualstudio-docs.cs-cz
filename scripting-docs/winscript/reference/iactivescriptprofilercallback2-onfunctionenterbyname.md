---
title: 'Iactivescriptprofilercallback2 –:: OnFunctionEnterByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571638"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Upozorní objekt profileru na to, že skriptovací stroj spustí volání funkce model DOM (Document Object Model) (DOM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 pro Název funkce, která se bude spouštět skriptovacím modulem.  
  
 `scriptType`  
 pro Typ funkce. Popisy platných hodnot naleznete v tématu [PROFILER_SCRIPT_TYPE Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Skriptovací stroj ignoruje vrácenou hodnotu této metody.  
  
## <a name="remarks"></a>Poznámky  
 Pro volání DOM skriptovací modul volá tuto metodu místo volání metody [iactivescriptprofilercallback –:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Důvodem je velký počet jedinečných metod a vlastností v modelu DOM.  
  
## <a name="see-also"></a>Viz také:  
 [Iactivescriptprofilercallback2 –:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)    
 [IActiveScriptProfilerCallback2 – rozhraní](../../winscript/reference/iactivescriptprofilercallback2-interface.md)