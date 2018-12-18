---
title: IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 797476d4892224ad0b27c9caf579c0704693c835
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793368"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Objekt, který skriptování modul zjistil funkce při kompilování skriptu oznamuje profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] Jedinečné ID funkce. Toto ID je přiřazena službou skriptovacího stroje.  
  
 `scriptId`  
 [v] Jedinečné ID skript, který je součástí funkce.  
  
 `pwszFunctionName`  
 [v] Název funkce nebo hodnota null pro anonymní funkce.  
  
 `pwszFunctionNameHint`  
 [v] Odvozené název funkce nebo hodnota null, pokud skriptovacího stroje nelze odvodit žádný název.  
  
 `pIDebugDocumentContext`  
 [v] Pokud je k dispozici, má ukazatel na `IUnknown` rozhraní, které musí vyhledat profileru [idebugdocumentcontext – rozhraní](../../winscript/reference/idebugdocumentcontext-interface.md) ukazatel. Jinak hodnota null.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota tato metoda je ignorován v skriptovacího stroje.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj může poskytnout kontext dokumentu pouze v případě, že to je podporováno pro hostitele.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptprofilercallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)