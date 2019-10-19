---
title: 'Iactivescriptprofilercallback –:: FunctionCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576477"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Upozorní objekt profileru, že skriptovací stroj zaznamenal funkci při kompilování skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 pro Jedinečné ID funkce Toto ID přiřadí skriptovací stroj.  
  
 `scriptId`  
 pro Jedinečné ID skriptu, jehož funkce je součástí.  
  
 `pwszFunctionName`  
 pro Název funkce nebo hodnota null pro anonymní funkci.  
  
 `pwszFunctionNameHint`  
 pro Odvozený název funkce, nebo hodnota null, pokud skriptovací modul neodvodí žádný název.  
  
 `pIDebugDocumentContext`  
 pro Je-li k dispozici, ukazatel na rozhraní `IUnknown`, které Profiler musí zadat dotaz na ukazatel [rozhraní idebugdocumentcontext –](../../winscript/reference/idebugdocumentcontext-interface.md) . V opačném případě hodnota null.  
  
## <a name="return-value"></a>Návratová hodnota  
 Skriptovací stroj ignoruje vrácenou hodnotu této metody.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj může poskytnout kontext dokumentu pouze v případě, že to hostitel podporuje.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerCallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)