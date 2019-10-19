---
title: 'Iactivescriptprofilercallback –:: ScriptCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571660"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Upozorní objekt profileru, že skriptovací stroj zkompiluje skript. Tato metoda je volána pro každý kompilovaný skript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 pro Jedinečné ID skriptu, který byl zkompilován. Toto ID přiřadí skriptovací stroj.  
  
 `type`  
 pro Typ skriptu, který byl zkompilován. Hodnoty jsou definovány ve [výčtu PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 pro Je-li k dispozici, ukazatel na `IUnknown` rozhraní, které Profiler musí zadat dotaz na ukazatel [rozhraní idebugdocumentcontext –](../../winscript/reference/idebugdocumentcontext-interface.md) . V opačném případě bude mít hodnotu null.  
  
## <a name="return-value"></a>Návratová hodnota  
 Skriptovací stroj ignoruje vrácenou hodnotu této metody.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj může poskytnout kontext dokumentu pouze v případě, že to hostitel podporuje.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerCallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)