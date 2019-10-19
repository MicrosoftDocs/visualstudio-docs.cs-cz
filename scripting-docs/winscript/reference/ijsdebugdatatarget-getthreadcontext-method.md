---
title: 'IJsDebugDataTarget:: GetThreadContext – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577649"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext – metoda
Načte kontext pro dané vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 pro Vlákno spuštěné v cílovém procesu.  
  
 `contextFlags`  
 pro Určuje kontextové příznaky. To je stejné jako pole ContextFlags kontextu (Další informace najdete v tématu Winnt. h, vyhledejte CONTEXT_ALL).  
  
 `contextSize`  
 pro Velikost vyrovnávací paměti určené parametrem pContext.  
  
 `pContext`  
 mimo Přijme strukturu kontextu specifickou pro platformu do vyrovnávací paměti určené parametrem pContext.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)