---
title: IActiveScriptError::GetSourcePosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d63310a8ba5cfda39d48a482eaf7c345cd492adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793344"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Načte umístění ve zdrojovém kódu, kde došlo k chybě skriptování modul byl spuštěn skript.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSourceContext`  
 [out] Adresa proměnné, která obdrží soubor cookie, který identifikuje kontextu. Výklad tento parametr závisí na hostitelskou aplikaci.  
  
 `pulLineNumber`  
 [out] Adresa proměnné, která obdrží číslo řádku ve zdrojovém souboru, kde došlo k chybě.  
  
 `pichCharPosition`  
 [out] Adresa proměnné, která přijímá pozice znaku v řádku, kde došlo k chybě.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu nebo `E_FAIL` Pokud umístění nebyla načtena.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescripterror –](../../winscript/reference/iactivescripterror.md)