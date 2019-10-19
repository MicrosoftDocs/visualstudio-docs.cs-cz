---
title: 'IJsDebugBreakPoint:: Getdocumentposition – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f3bc5aff0b7079e20e2bcd49189153d2ec20d9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577698"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>IJsDebugBreakPoint::GetDocumentPosition – metoda
Vrátí pozici příkazu, kde byla zarážka svázána.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocumentId`  
 mimo Jedinečné ID zdrojového dokumentu (ukazatel na IDebugDocumentText –).  
  
 `pCharacterOffset`  
 mimo Posun znaku založený na nule od začátku skriptu.  
  
 `pStatementCharCount`  
 mimo Délka aktuálního příkazu, který začíná na * pCharacterOffset, ve znacích.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugBreakPoint – rozhraní](../../winscript/reference/ijsdebugbreakpoint-interface.md)