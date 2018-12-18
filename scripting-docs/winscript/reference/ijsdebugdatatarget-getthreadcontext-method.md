---
title: Ijsdebugdatatarget::getthreadcontext – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4e2f858c66eda2ad09b04d7beab776c793b6f195
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794607"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext – metoda
Načte kontext pro danou přístup z více vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [v] Přístup z více vláken spuštěných v procesu cíl.  
  
 `contextFlags`  
 [v] Určuje příznaky kontextu. Toto je stejné jako pole ContextFlags kontextu (pro další informace naleznete v souboru winnt.h, vyhledejte CONTEXT_ALL).  
  
 `contextSize`  
 [v] Velikost vyrovnávací paměti určeného pContext.  
  
 `pContext`  
 [out] Obdrží specifické pro platformu kontextu struktura do určeného pContext vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugdatatarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)