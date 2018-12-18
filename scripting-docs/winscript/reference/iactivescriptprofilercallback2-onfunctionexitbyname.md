---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: dd26ab1cf36378c0f037d78a3c079c58e004006d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794376"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Objekt, který skriptování modul spuštění volání funkce modelu DOM (Document Object) dokončeno oznamuje profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 [v] Název funkce ukončen skriptovacího stroje.  
  
 `scriptType`  
 [v] Typ funkce. Popis platných hodnot najdete v tématu [PROFILER_SCRIPT_TYPE – výčet](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota tato metoda je ignorován v skriptovacího stroje.  
  
## <a name="remarks"></a>Poznámky  
 Pro volání DOM skriptovacího stroje volá tuto metodu namísto volání [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Je to z důvodu velkého počtu jedinečných metody a vlastnosti v modelu DOM.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [Iactivescriptprofilercallback2 – rozhraní](../../winscript/reference/iactivescriptprofilercallback2-interface.md)