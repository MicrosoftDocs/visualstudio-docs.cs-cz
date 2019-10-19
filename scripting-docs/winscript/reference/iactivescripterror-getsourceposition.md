---
title: 'IActiveScriptError:: GetSourcePosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576888"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Načte umístění ve zdrojovém kódu, kde došlo k chybě, když skriptovací stroj spustil skript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSourceContext`  
 mimo Adresa proměnné, která přijímá soubor cookie, který identifikuje kontext. Výklad tohoto parametru závisí na hostitelské aplikaci.  
  
 `pulLineNumber`  
 mimo Adresa proměnné, která přijímá číslo řádku ve zdrojovém souboru, kde došlo k chybě.  
  
 `pichCharPosition`  
 mimo Adresa proměnné, která přijímá pozici znaku na řádku, kde došlo k chybě.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud bylo úspěšné, nebo `E_FAIL`, pokud nebylo umístění načteno.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)